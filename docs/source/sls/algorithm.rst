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

第一个扩展(SCI)的数据单元存放着仪器效应改正后的光谱图像，第二扩展(ERR)的数据单元存放着光谱图像误差，第三个扩展（DQ）的数据单元存放着光谱图像每个像素的数据质量标志位，具体参见 DQFlags_。仪器效应改正过程中，同时会记录下处理时间、状态信息等关键字，具体参见 DataModel_。

.. _DQFlags: https://？

Data Calibration Steps
``````````````````
仪器效应改正包括以下步骤：
    DQ Initialization
    ''''''''''''''''''



Position calibration
---------------------

`csst_ms_sls_position` package.


API
---

TODO
