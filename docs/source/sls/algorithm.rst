SLS pipeline
============


Instrument correction
---------------------

概述
``````````````````
`csst_ms_sls_instrument` 程序包是应用于CSST无缝光谱模块的仪器效应改正程序，无缝光谱模块包含12个探测器，每4块探测器对应1个波段，每个波段的部分仪器参数如下：

    - GU: 660×660″ field of view from 255-400nm with a plate scale of 0.07″/pixel
    - GV: 660×660″ field of view from 400-620nm with a plate scale of 0.07″/pixel
    - GI: 660×660″ field of view from 620-1000nm with a plate scale of 0.07″/pixel
该程序将顺序执行一系列的探测器效应改正，生成单次曝光的改正后数据产品。该程序是用Python语言实现，代码地址：code_。

.. _code: https://csst-tb.bao.ac.cn/code/csst-l1/sls/csst_ms_sls_instrument

数据产品
``````````````````


Position calibration
---------------------

`csst_ms_sls_position` package.


API
---

TODO
