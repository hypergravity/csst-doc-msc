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
````````````````````````
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
Description
``````````````````
`csst_ms_sls_position` 程序包是应用于CSST无缝光谱模块的位置定标程序，无缝光谱模块包含12块9k×9k探测器，分为3个波段GU
、GV、GI，执行一系列的探测器效应改正，生成单次曝光图像预处理后的数据产品。该程序依赖Python 3.9+实现，代码地址：code_。

code: https://csst-tb.bao.ac.cn/code/csst-l1/sls/csst_ms_sls_position

Input
``````````````````
`csst_ms_sls_position` 将从csst_common.CsstMsDataManager获取仪器效应改正后的L0.5级数据和定标参考文件。

1. L0.5级数据: 包含一个扩展的fits文件，header文件中望远镜观测指向信息：CD系数、CRVAL、CRPIX数据等； 扩展的data单元存放着仪器效应改正后的观测SCI图像、ERR、DQ数据。
2. 位置定标参考文件: 位置定标中所需的参考文件目前选取同视场gaia dr3恒星星表，其中包含恒星的位置信息，视差及其误差，自行及其误差。


Output
``````````````````
`csst_ms_sls_position` 生成的结果主要包含位置信息参数、畸变系数、位置定标评估信息、状态信息，更新在SCI扩展的header文件中，具体DataModel如下：

.. _DataModel: https://csst-tb.bao.ac.cn/code/csst-l1/csst-l1doc/-/blob/main/docs/source/sls/data_model.md

+----------+-----------------------+------------------------------------------+
| keyword  | value                 | comment                                  |
+==========+=======================+==========================================+
| VER_POS  | '1.0'                 | Version of distortion                    |
+----------+-----------------------+------------------------------------------+
| STM_POS  | '2023-02-16 12:15:16' | Time of last modification                |
+----------+-----------------------+------------------------------------------+
| STA_POS  | 0                     | 0 for done, 1 for failure                |
+----------+-----------------------+------------------------------------------+
| CRPIX1   | 29758.0               | Coordinate reference pixel of x          |
+----------+-----------------------+------------------------------------------+
| CRPIX2   | -15644.0              | Coordinate reference pixel of y          |
+----------+-----------------------+------------------------------------------+
| CRVAL1   | 193.299027            | Coordinate reference value of x          |
+----------+-----------------------+------------------------------------------+
| CRVAL2   | 26.08851              | Coordinate reference value of y          |
+----------+-----------------------+------------------------------------------+
| CTYPE1   | 'RA---TPV'            | Type of ra                               |
+----------+-----------------------+------------------------------------------+
| CTYPE2   | 'DEC--TPV'            | Type of dec                              |
+----------+-----------------------+------------------------------------------+
| CD1_1_L0 | -8.1745583617600E-06  | Partial of first axis coordinate of x    |
+----------+-----------------------+------------------------------------------+
| CD2_1_L0 | 1.88602083707394E-05  | Partial of first axis coordinate of y    |
+----------+-----------------------+------------------------------------------+
| CD1_2_L0 | -1.8860208370739E-05  | Partial of second axis coordinate of x   |
+----------+-----------------------+------------------------------------------+
| CD2_2_L0 | -8.1745583617600E-06  | Partial of second axis coordinate of y   |
+----------+-----------------------+------------------------------------------+
| CD1_1    | -8.1745583617600E-06  | Partial of first axis coordinate of x    |
+----------+-----------------------+------------------------------------------+
| CD2_1    | 1.88602083707394E-05  | Partial of first axis coordinate of y    |
+----------+-----------------------+------------------------------------------+
| CD1_2    | -1.8860208370739E-05  | Partial of second axis coordinate of x   |
+----------+-----------------------+------------------------------------------+
| CD2_2    | -8.1745583617600E-06  | Partial of second axis coordinate of y   |
+----------+-----------------------+------------------------------------------+
| CUNIT1   | 'deg  '               | Unit of ra                               |
+----------+-----------------------+------------------------------------------+
| CUNIT2   | 'deg  '               | Unit of dec                              |
+----------+-----------------------+------------------------------------------+
| RADESYS  | 'ICRS '               | International celestial reference system |
+----------+-----------------------+------------------------------------------+
| PV1_0    | 0.003205383944913964  | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV1_1    | 0.8673020820536499    | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV1_2    | -0.2011989871377834   | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV1_3    | -0.2597214229472611   | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV1_4    | 0.4353828741811097    | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV1_5    | -0.5054216569802673   | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV1_6    | 0.1951474426617432    | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV2_0    | 0.00109803885992697   | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV2_1    | 0.9171065857705857    | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV2_2    | -0.04908256792722099  | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV2_3    | -0.09860562038448289  | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV2_4    | 0.07961855240788976   | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV2_5    | -0.2009224365497067   | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| PV2_6    | 0.1741954691884874    | PV coefficients                          |
+----------+-----------------------+------------------------------------------+
| NS_POS   | 10                    | Number of the stars                      |
+----------+-----------------------+------------------------------------------+
| RA_OFF   | -0.0                  | Mas in unit                              |
+----------+-----------------------+------------------------------------------+
| DEC_OFF  | 0.0                   | Mas in unit                              |
+----------+-----------------------+------------------------------------------+
| RA_RMS   | 127.1                 | Mas in unit                              |
+----------+-----------------------+------------------------------------------+
| DEC_RMS  | 60.4                  | Mas in unit                              |
+----------+-----------------------+------------------------------------------+
| RA_CEN   | 193.299027            | Center of detector in ra                 |
+----------+-----------------------+------------------------------------------+
| DEC_CEN  | 26.08851              | Center of detector in dec                |
+----------+-----------------------+------------------------------------------+


Position Calibration
^^^^^^^^^^^^^^^^^^^^

`csst_ms_sls_position` 模块主要定标过程分以下四部分组成：

1.点源目标提取

    由于CSST无缝光谱和多色成像共焦面排布，对于无缝光谱的位置定标只能选取无缝光谱视场内的点源零级像作为目标天体，csst_ms_sls_position模块选取photutils模块中的DAOStarFinder提取零级像点源目标。获得零级像后的目标，根据目标所在CCD位置的区域（2/5,3/5）对应的色散关系反推零级像的直接像的像素位置。

2.和位置定标参考星标匹配

    获得零级像的直接像像素位置（x, y）星表后，通过L05数据中望远镜观测wcs信息CD系数、CRVAL、CRPIX，可获取直接像UV平面的位置信息，同时也可将参考星表历元改正后的（ra,dec），通过wcs信息映射到UV平面，通过xyxy_match方法在对上述直接像和参考星在UV平面进行匹配配对。

3.迭代拟合畸变模式

    获得配对后的位置星表，拟合二元二阶多项式畸变关系，并使用畸变关系改正初始直接像星表的uv位置，进一步同参考星表进行步骤2的匹配配对，配对后再次拟合畸变关系，迭代上述过程直到在给定范围内匹配得到的恒星数量不再变化，最终拟合得到相应的畸变系数。

4.输出更新header中位置定标关键字

    通过判定步骤3中最终位置定标所采用的恒星数量是否大于10颗，将判定拟合过程是否正常运行，如大于10，表示正常运行，按照data model定义更新L1 header文件中的position calibration information关键字信息；否则，按照data model默认值更新L1 header文件中的position calibration information关键字信息；最终输出保存L1级fits文件。

