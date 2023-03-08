SLS pipeline
============


Instrument correction
---------------------

Description
``````````````````
`csst_ms_sls_instrument` 程序包是应用于CSST无缝光谱模块的仪器效应改正程序，无缝光谱模块包含12块9k×9k探测器，每4块探测器对应1个波段，每个波段的部分仪器参数如下：

    - GU: 660×660″ field of view from 255-400nm with a plate scale of 0.074″/pixel
    - GV: 660×660″ field of view from 400-620nm with a plate scale of 0.074″/pixel
    - GI: 660×660″ field of view from 620-1000nm with a plate scale of 0.074″/pixel
`csst_ms_sls_instrument` 将顺序执行一系列的探测器效应改正，生成单次曝光图像预处理后的数据产品。该程序是用Python语言实现，代码地址：code_。

.. _code: https://csst-tb.bao.ac.cn/code/csst-l1/sls/csst_ms_sls_instrument
Input
``````````````````
`csst_ms_sls_instrument` 将从csst_common.CsstMsDataManager获取0级数据和参考文件。

1. 0级数据: 包含一个扩展的fits文件，头文件中存放着观测天区、曝光信息、探测器信息等，具体关键字说明参见 DataModel_，扩展的数据单元存放着原始观测图像。
#. 参考文件: 仪器效应改正中所需的参考文件如下表所示。

+-----------------+----------------------------+
| Reference file  | Description                |
+=================+============================+
| Gain map        | gain array(9k×9k)          | 
+-----------------+----------------------------+
| Superbias       | superbias file(9k×9k)      | 
+-----------------+----------------------------+
| Superdark       | superdark file(9k×9k)      |
+-----------------+----------------------------+
| Superflat       | super flatfield file(9k×9k)|
+-----------------+----------------------------+
| Badpixel table  | Bad/hot Pixel table or map |
+-----------------+----------------------------+

.. _DataModel: https://csst-tb.bao.ac.cn/code/csst-l1/csst-l1doc/-/blob/main/docs/source/sls/data_model.md

Output
``````````````````
`csst_ms_sls_instrument` 生成的数据产品是包含三个扩展的fits文件，扩展内容如下表所示：

+-----------------+---------+-------------------+
| Extension name  |  Bunit  | Comment           |
+=================+=========+===================+
| SCI             | e-/s    | Science image     |
+-----------------+---------+-------------------+
| ERR             | e-/s    | Error array       |
+-----------------+---------+-------------------+
| DQ              | unitless| Data quality array|
+-----------------+---------+-------------------+

第一个扩展(SCI)的数据单元存放着仪器效应改正后的光谱图像，第二扩展(ERR)的数据单元存放着光谱图像误差，第三个扩展（DQ）的数据单元存放着光谱图像每个像素的数据质量标志位，具体参见 DQFlags_，DQFlags应包含下表的三项。仪器效应改正过程中，同时会记录下处理时间、状态信息等关键字，具体参见 DataModel_。

.. _DQFlags: https://？

+----------------+---------+---------------------------------------------+
| TTYPE          | TFORM   |  Description                                |
+================+=========+=============================================+
| BIT            | integer | The bit number, starting at zero            |
+----------------+---------+---------------------------------------------+
| VALUE          | integer | The equivalent base-10 value of BIT         |
+----------------+---------+---------------------------------------------+
| DESCRIPTION    | string  |  A description of the data quality condition|
+----------------+---------+---------------------------------------------+

Data Calibration Steps
``````````````````
仪器效应改正包括以下步骤：

**DQ Initialization**

class： csst_ms_sls_instrument.steps.DQIstep

reference file： Badpixel table(map)、Saturation file

DQ Initialization实现两部分内容，一是利用参考文件Badpixel table或是Badpixel map对DQ扩展进行标记，该参考文件记录着存在问题的像素点，可能是探测器的坏点、热像素。二是根据Saturation file对观测数据进行判定，并在DQ扩展中标记。Saturation file的形式需要根据后续测试结果来定，如果能测出每个像素的饱和值即可做成map，现阶段用的是常值。DQ标记的详情参见 DQFlags_。

**Bias correction**

class： csst_ms_sls_instrument.steps.BiasCorrStep

reference file：Superbias

Bias correction通过减去superbias的操作，去除掉原始科学数据中的探测器本底。Superbias的文件格式与输出文件一致，为包含三个扩展的fits。该步会对superbias的误差和DQ进行传递。

**To electrons**

class： csst_ms_sls_instrument.steps.ToElectronsStep

reference file: Gain map

数据乘以增益，SCI数据单元和ERR数据单元的单位由ADU转换为电子。

**Uncertainty Initialization**

class: csst_ms_sls_instrument.steps.UncertaintyInitStep

reference file: readnoise file

ERR数据单元构造误差数据，该步误差公式：

.. math:: \sigma = \sqrt{(SCI-bias)+{\sigma_bias}^2 + readnoise^2} 


**Dark correction**

class: csst_ms_sls_instrument.steps.DarkCorrStep

reference file：Superdark

Dark correction通过减去superdark的操作，去除掉原始科学数据中的探测器暗电流。Superdark的文件格式与输出文件一致，为包含三个扩展的fits。该步会对superdark的误差和DQ进行传递。

**Flatfield correction**

class: csst_ms_sls_instrument.steps.FlatCorrStep

reference file：Superflat

Flatfield correction通过除flatfield的操作，去除掉像素不均匀性。Superflat的文件格式与输出文件一致，为包含三个扩展的fits。该步会对superflat的误差和DQ进行传递。

**CR rejection**

class: csst_ms_sls_instrument.steps.CRrejStep

reference file：cr model 

CR rejection基于无缝光谱图像训练的模型，利用 deepCR_ 对单次曝光的科学数据进行宇宙线检测，在DQ中进行标记，标记详情见 DQFlags_ 。

.. _deepCR: https://deepcr.readthedocs.io/en/latest/

**To electrons/sec**

class: csst_ms_sls_instrument.steps.CPSStep

reference file：无

数据除以曝光时间，SCI数据单元和ERR数据单元的单位由e转换为e/s。



Position calibration
---------------------

`csst_ms_sls_position` package.


API
---

TODO
