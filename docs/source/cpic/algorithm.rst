CPI-C pipeline
==============

-CPI-C只包含仪器效应改正、宇宙线改正和天光背景改正。

仪器改正
--------

`csst_cpic` package 的一部分.

-过程：增益/EM增益改正→CTE改正→溢出像素识别→坏点识别→overscan改正→偏置改正→CIC改正→暗电流改正→平场改正→非线性改正→溢出拖尾改正

宇宙线改正
----------

`csst_cpic` package 的一部分.


-方法：使用crmask.py模块，该模块使用lacosmic或deepCR模块进行宇宙线识别。
-参数：使用crmask.ini。


天光背景改正
----------------

`csst_cpic` package 的一部分.

-数据：CRDS提供的天光背景改正图像
-处理方法：使用科学图像与天光背景改正图像相减。