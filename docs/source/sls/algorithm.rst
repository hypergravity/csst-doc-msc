SLS pipeline
============


Instrument correction
---------------------

CSST SLS pipeline是应用于12块无缝光谱模块探测器的仪器效应改正，包含3个波段，每4块探测器对应1个波段：

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
