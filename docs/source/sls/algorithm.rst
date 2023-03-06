SLS pipeline
============


Instrument correction
---------------------

概述
``````````````````
`csst_ms_sls_instrument` 程序包是应用于CSST无缝光谱模块的仪器效应改正程序，无缝光谱模块包含12块9k×9k探测器，每4块探测器对应1个波段，每个波段的部分仪器参数如下：

    - GU: 660×660″ field of view from 255-400nm with a plate scale of 0.074″/pixel
    - GV: 660×660″ field of view from 400-620nm with a plate scale of 0.074″/pixel
    - GI: 660×660″ field of view from 620-1000nm with a plate scale of 0.074″/pixel
`csst_ms_sls_instrument` 将顺序执行一系列的探测器效应改正，生成单次曝光图像预处理后的数据产品。该程序是用Python语言实现，代码地址：code_。

.. _code: https://csst-tb.bao.ac.cn/code/csst-l1/sls/csst_ms_sls_instrument

数据产品
``````````````````
`csst_ms_sls_instrument` 生成的数据产品是三个扩展fits文件，扩展内容如下表所示：

+-----------------+---------+-------------------+
| Extension name  |  Bunit  | Comment           |
+=================+=========+===================+
| SCI             | e-/s    | Science image     |
+-----------------+---------+-------------------+
| ERR             | e-/s    | Error array       |
+-----------------+---------+-------------------+
| DQ              | unitless| Data quality array|
+-----------------+---------+-------------------+

第一个扩展(SCI)的数据单元存放着仪器效应改正后的光谱图像，第二扩展(ERR)的数据单元存放着光谱图像误差，第三个扩展（DQ）的数据单元存放着光谱图像每个像素的数据质量标志位，具体参见 DQFlags_。

.. _DQFlags: https://？

处理过程
``````````````````
`csst_ms_sls_instrument` 将从`csst_common.CsstMsDataManager` 获取0级数据和参考文件。0级数据是有一个扩展的fits文件，头文件中存放着观测天区、曝光信息、探测器信息等，具体关键字说明参见 DataModel_，扩展的数据单元存放着原始观测图像。参考文件列表如下,第一列是参考文件类型，第二列是文件说明，第三列是数据产品中记录文件名的关键字：

+-----------------+----------------------------+-----------------+
| Reference file  | Description                | Keyword         |
+=================+============================+=================+
| Gain map        | gain array(9k×9k)          | R_GAIN          |
+-----------------+----------------------------+-----------------+
| Superbias       | superbias file(9k×9k)      | R_BIAS          |
+-----------------+----------------------------+-----------------+
| Superdark       | superdark file(9k×9k)      | R_DARK          |
+-----------------+----------------------------+-----------------+
| Superflat       | super flatfield file(9k×9k)| R_DFLAT         |
+-----------------+----------------------------+-----------------+
| Badpixel table  | Bad/hot Pixel table or map | R_MASK          |
+-----------------+----------------------------+-----------------+

.. _DataModel: https://csst-tb.bao.ac.cn/code/csst-l1/csst-l1doc/-/blob/main/docs/source/sls/data_model.md



Position calibration
---------------------

`csst_ms_sls_position` package.


API
---

TODO
