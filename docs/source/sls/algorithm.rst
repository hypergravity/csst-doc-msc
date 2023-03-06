SLS pipeline
============


Instrument correction
---------------------

    `csst_ms_sls_instrument`程序包是应用于CSST无缝光谱模块的仪器效应改正程序，无缝光谱模块包含12个探测器，每4块探测器对应1个波段，每个波段的部分仪器参数如下：

    - GU: ″ field of view from 255-400nm with a plate scale of ″/pixel.
    - GV: ″ field of view from 400-620nm with a plate scale of ″/pixel.
    - GI: ″ field of view from 620-1000nm with a plate scale of ″/pixel.
    pipeline顺序执行一系列的效应改正，生成单次曝光的改正后数据产品。该程序是用Python语言实现，开源地址：。


Position calibration
---------------------

`csst_ms_sls_position` package.


API
---

TODO
