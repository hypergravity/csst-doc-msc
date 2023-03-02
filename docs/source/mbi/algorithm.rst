MBI pipeline
============


仪器改正
-------

`csst_ms_mbi_instrument` package.


位置定标
-------
`csst_ms_mbi_distortion` and `csst_ms_mbi_position` package.


- 该模块采用了什么算法？例如MCMC，kd-tree-该算法，必要时附上公式和算法链接。
- 为什么要采用该算法？
- 该算法的优势是什么？缺点是什么？例如计算性能和误差分析
- 该算法参考了什么数据/星表？ 例如Gaia DR3
- 该算法是否使用了第三方软件？如有，请提供必要的软件介绍和软件网站链接。例如scamp  sextractor
- 该算法使用了什么样的假设？为什么？例如假设A与B相互独立，C是A与B的函数。
- 该算法考虑了哪些效应？忽略了哪些效应？例如BIAS CTE
- 算法有哪些参数设定？为什么要如此设定？例如多项式阶数、等。例如为什么不能设定10阶多项式
- 该算法产生的数据产品是什么？核心关键字和数据的介绍（与一级data model的对应）
- 该算法在测试中的性能如何？
    - 计算性能：目前速度，是否可优化
    - 科学指标：目前精度，未来是否有提高可能
- 与国际前沿算法的比较？
- 该模块未来的升级方向？ 利用机器学习？
- 该模块与其他同类设备的对应模块有何异同? HST JWST
- **请提供需要的文献信息 ! 各种网址和文献的ADS链接**


流量定标
----------------

`csst_ms_mbi_flux` package.

使用csst_ms_mbi_position生成的星表，
利用wcs.head中的畸变系数重新计算了星表的位置信息。
目前的参考星表是输入的cat文件，未来计划替换为gaia，pansstar等星表混合成的参考星表文件


测光
---

`csst_ms_mbi_photometry` package.


Astrometry
----------

`csst_ms_mbi_astrometry` package.
