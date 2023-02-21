MBI pipeline
============


Instrument correction
---------------------

`csst_ms_mbi_instrument` package.

Position calibration
---------------------

`csst_ms_mbi_distortion` and `csst_ms_mbi_position` package.


Flux calibration
----------------

`csst_ms_mbi_flux` package.
使用csst_ms_mbi_position生成的星表，利用wcs.head中的畸变系数重新计算了星表的位置信息。目前的参考星表是输入的cat文件，未来计划替换为gaia，pansstar等星表混合成的参考星表文件


Photometry
----------

`csst_ms_mbi_photometry` package.


Astrometry
----------

`csst_ms_mbi_astrometry` package.


API
---

TODO
