# L1-MBI Data model

- 每一个模块的结果单独开一个section，以COMMENT分隔（参考0级数据）
- 精简、丰富、修改每个关键字定义的comment
- `---`表示在模块算法失败的情况下按照实际情况填写，比如无论模块是否成功，时间戳都应该填写实际值
- keyword开头是“-”号的，根据理解和最终的产品无关，建议去掉
- keyword开头是“*”号的，表示有所修改，请检查是否需要，完善注释，并检查对fill value的设置是否合理
- flux模块中的天光背景测量已经移动到instrumens，请把该数值利用zp转换为SKY_MAG（单位mag/arcsed^2）
- 版本，完成时间，状态三个参数的name进行了统一，分别以VER_，STM_，STA_开头

## File: *_{img/wht/flg}_L1_1.fits

### File contents

| HDU  | data                    | note       |
|------|-------------------------|------------|
| HDU0 | None                    | PrimaryHDU |
| HDU1 | reduced image (9k x 9k) | ImageHDU   |

### HDU0

| keyword | value | comment       | fill value    | type | module    |
|---------|:------|---------------|---------------|------|-----------|
| SIMPLE  | True  | Fits standard | True          | bool | csst_sims |     

### HDU1

#### Header of `csst_ms_mbi_instrument`

| keyword   | value                 | comment                                         | fill value   | type | module                   |
|-----------|:----------------------|-------------------------------------------------|--------------|------|--------------------------|
|  VER_INST | '0.0.1   '            | Version of instrument processing                | '0.0.1   '   | str  | csst_ms_mbi_instrument   |
|  STA_INST | 0                     | 0=done 1=wrong                                  | 1            | i8   | csst_ms_mbi_distortion   | 
|  STM_INST | '2022-12-30T10:18:53' | Time stamp of instrument processing             | ---          | str  | csst_ms_mbi_instrument   |
|  DATASUM  | '1352015684'          | data unit checksum                              | ---          | str  | csst_ms_mbi_instrument   |
|  STA_BIAS | 0                     | Status flag for bias frame correction           | 1            | i8   | csst_ms_mbi_instrument   |
|  STA_DARK | 0                     | Status flag for dark frame correction           | 1            | i8   | csst_ms_mbi_instrument   |
|  STA_FLAT | 0                     | Status flag for flat frame correction           | 1            | i8   | csst_ms_mbi_instrument   |
|  SKY_BKG  | 0.1                   | Estimated sky background (e-/s per pixel)       | -9999        | f32  | csst_ms_mbi_instrument   |
|  SKY_RMS  | 10.0                  | *Standard dev of frame background (ADU) -> e-/s | -9999        | f32  | csst_ms_mbi_instrument   |        
|  SATURATE | 1833.333333333333     | The flux limit of saturated pixel (e-/s)        | -9999        | f32  | csst_ms_mbi_instrument   |
|  STA_CTE  | 0                     | Status flag for CTE correction                  | 1            | i8   | csst_ms_mbi_instrument   |
|  STA_SAT  | 0                     | Status flag for satellite correction            | 1            | i8   | csst_ms_mbi_instrument   |
|  STA_CRS  | 0                     | Status flag for cosmic rays mask                | 1            | i8   | csst_ms_mbi_instrument   |
|  CRCOUNT  | 66791                 | Cosmic rays counts                              | -9999        | i8   | csst_ms_mbi_instrument   |
|  STA_NLIN | 0                     | Status flag for non-linear correction           | 1            | i8   | csst_ms_mbi_instrument   |
|  STA_SHUT | 0                     | Status flag for shutter effect correction       | 1            | i8   | csst_ms_mbi_instrument   |

#### Header of `csst_ms_mbi_distortion`

| keyword  | value                 | comment                             | fill value | type | module                 |
|----------|:----------------------|-------------------------------------|------------|------|------------------------|
| VER_DIST | '1.0     '            | Version of distortion               | '1.0'      | str  | csst_ms_mbi_distortion |
| STA_DIST | 0                     | 0=done 1=wrong                      | 1          | i8   | csst_ms_mbi_distortion | 
| STM_DIST | '2022-12-29T16:36:47' | Time stamp of distortion            | ---        | str  | csst_ms_mbi_distortion |
| RADESYS  | 'ICRS    '            |                                     | '?'        | str  | csst_ms_mbi_distortion |
| CRPIX1   |                -267.0 | Coordinate reference pixel of x     | -267.0     | f32  | csst_ms_mbi_distortion |
| CRPIX2   |               14746.0 | Coordinate reference pixel of y     | 14746.0    | f32  | csst_ms_mbi_distortion |  
| CRVAL1   |                  90.0 | Coordinate reference value of x     | 90.0       | f32  | csst_ms_mbi_distortion |
| CRVAL2   |                  24.5 | Coordinate reference value of y     | 24.5       | f32  | csst_ms_mbi_distortion |  
| CTYPE1   | 'RA---TPV'            | the coordinate type                 | 'RA---TAN' | f32  | csst_ms_mbi_distortion |        
| CTYPE2   | 'DEC--TPV'            | the coordinate type                 | 'DEC--TPV' | f32  | csst_ms_mbi_distortion |
| CD1_1    | -8.1745583617600E-06  | partial of first axis coordinate of x | -8.1745583617600E-06 | f32 | csst_ms_mbi_distortion |
| CD2_1    | 1.88602083707394E-05  | partial of first axis coordinate of y | 1.88602083707394E-05 | f32 | csst_ms_mbi_distortion |       
| CD1_2    | -1.8860208370739E-05  | partial of second axis coordinate of x | -1.8860208370739E-05 | f32 | csst_ms_mbi_distortion |        
| CD2_2    | -8.1745583617600E-06  | partial of second axis coordinate of y | -8.1745583617600E-06 | f32 | csst_ms_mbi_distortion |     
| NS_DIST  | 11                    | The number of stars used in fitting | ---        | i8   | csst_ms_mbi_distortion | 
| PV1_0    | 0.003205383944913964  |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV1_1    | 0.8673020820536499    |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV1_2    | -0.2011989871377834   |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV1_3    | -0.2597214229472611   |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV1_4    | 0.4353828741811097    |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV1_5    | -0.5054216569802673   |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV1_6    | 0.1951474426617432    |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV2_0    | 0.00109803885992697   |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV2_1    | 0.9171065857705857    |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV2_2    | -0.04908256792722099  |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV2_3    | -0.09860562038448289  |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV2_4    | 0.07961855240788976   |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV2_5    | -0.2009224365497067   |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| PV2_6    | 0.1741954691884874    |                                     | -9999      | f32  | csst_ms_mbi_distortion |
| RA_OFF   | -0.0                  | RA offset (mas)                     | -9999      | f32  | csst_ms_mbi_distortion |
| DEC_OFF  | 0.0                   | Dec offset (mas)                    | -9999      | f32  | csst_ms_mbi_distortion |
| RA_RMS   | 127.1                 | RA RMS (mas)                        | -9999      | f32  | csst_ms_mbi_distortion |
| DEC_RMS  | 60.4                  | Dec RMS (mas)                       | -9999      | f32  | csst_ms_mbi_distortion |
| RA_CEN   | 192.1940713422841     | The center of detector in ra        | ---        | f32  | csst_ms_mbi_distortion |
| DEC_CEN  | 26.72643742371229     | The center of detector in dec       | ---        | f32  | csst_ms_mbi_distortion |

#### Header of `csst_ms_mbi_position`

| keyword   | value                    | comment                                    | fill value | type | module                  |
|-----------|:-------------------------|--------------------------------------------|------------|------|-------------------------|
| VER_POSI  | '2.0.4   '               | Version of WCS calibration                 | '2.0.4   ' | str  | csst_ms_mbi_position    |        
| STA_POSI  | 0                        | 0=done                                     |            | i8   | csst_ms_mbi_position    | 
| STM_POSI  | '2022-12-30 18:32:46 PM' | Time of last wcs calibration               | ---        | str  | csst_ms_mbi_position    |             
| RADESYS   | 'ICRS    '               | should be always 'ICRS'                    | '?'        | str  | csst_ms_mbi_position    |
| CRPIX1   |                -267.0 | Coordinate reference pixel of x     | -267.0     | f32  | csst_ms_mbi_position |
| CRPIX2   |               14746.0 | Coordinate reference pixel of y     | 14746.0    | f32  | csst_ms_mbi_position |  
| CRVAL1   |                  90.0 | Coordinate reference value of x     | 90.0       | f32  | csst_ms_mbi_position |
| CRVAL2   |                  24.5 | Coordinate reference value of y     | 24.5       | f32  | csst_ms_mbi_position |  
| CTYPE1   | 'RA---TPV'            | the coordinate type                 | 'RA---TAN' | f32  | csst_ms_mbi_position |        
| CTYPE2   | 'DEC--TPV'            | the coordinate type                 | 'DEC--TPV' | f32  | csst_ms_mbi_position |
| CD1_1    | -8.1745583617600E-06  | partial of first axis coordinate of x | -8.1745583617600E-06 | f32 | csst_ms_mbi_position |
| CD2_1    | 1.88602083707394E-05  | partial of first axis coordinate of y | 1.88602083707394E-05 | f32 | csst_ms_mbi_position |       
| CD1_2    | -1.8860208370739E-05  | partial of second axis coordinate of x | -1.8860208370739E-05 | f32 | csst_ms_mbi_position |        
| CD2_2    | -8.1745583617600E-06  | partial of second axis coordinate of y | -8.1745583617600E-06 | f32 | csst_ms_mbi_position |     
| PV1_0     | -7.032303876526E-04      |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV1_1     | 9.986639936274E-01       |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV1_2     | -3.506141592607E-03      |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV1_4     | -2.342575913122E-03      |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV1_5     | -2.216829433925E-03      |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV1_6     | -5.122207406521E-03      |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV2_0     | -6.939462894407E-04      |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV2_1     | 9.988294486003E-01       |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV2_2     | -1.687802061938E-03      |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV2_4     | 1.561587727533E-03       |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV2_5     | -4.159618376671E-03      |                                            | -9999      | f32  | csst_ms_mbi_position    |
| PV2_6     | 3.398895060382E-03       |                                            | -9999      | f32  | csst_ms_mbi_position    |
| ASTRRMS1  | 6.458653303335E-06       | Astrom. dispersion RMS (ref., high S/N)    |            | f32  | csst_ms_mbi_position    |
| ASTRRMS2  | 8.724734011714E-06       | Astrom. dispersion RMS (ref., high S/N)    |            | f32  | csst_ms_mbi_position    |       

#### Header of `csst_ms_mbi_flux`

| keyword     | value                 | comment                                        | fill value      | type | module             |
|-------------|:----------------------|------------------------------------------------|-----------------|------|--------------------|
| VER_FLUX    | '1.3     '            | version of calibration code                    | '1.3'           | str  | csst_ms_mbi_flux   |
| STA_FLUX    | 0                     | flux calibration status                        | 1               | i8   | csst_ms_mbi_flux   |                       
| STM_FLUX    | '2022-12-30 18:36:05' | flux calibration operation time                | ---             | str  | csst_ms_mbi_flux   |
| REF_FLUX    | 'GAIA_DR3  '          | the reference database for calibration         | '?'             | str  | csst_ms_mbi_flux   |
| ZP          | 23.8435               | photometric zero point in magnitude            | -9999           | f32  | csst_ms_mbi_flux   |
| ZPRMS       | 0.0101                | zpt rms of the matched objects                 | -9999           | f32  | csst_ms_mbi_flux   |                
| APER_R      | 10                    | (pixels) photo-aperture radius                 | 10              | i8   | csst_ms_mbi_flux   |            
| FWHM        | 2.147                 | FWHM in pixel                                  | -9999           | f32  | csst_ms_mbi_flux   |
| RA_OFF1     | -0.188                | median positional offset from GAIA, in arcsec  | -9999           | f32  | csst_ms_mbi_flux   |
| DEC_OFF1    | -0.1061               | median positional offset from GAIA, in arcsec  | -9999           | f32  | csst_ms_mbi_flux   | 
| NS_FLUX     | 49                    | total number of stars detected                 | ---             | i8   | csst_ms_mbi_flux   | 
| NS_MATCH    | 25                    | total number of matched stars in 2 arcsec      | ---             | i8   | csst_ms_mbi_flux   |
| MED_CLR     | 0.0                   | median (BP-RP)_GAIA of matched stars           | -9999           | f32  | csst_ms_mbi_flux   |
| SKY_MAG     | 0.0359                | mag/arcsec^2                                   | -9999           | f32  | csst_ms_mbi_flux   |                 
| MAG_LIM     | 21.83                 | magnitude limiting of 5-sigma galaxy detection | -9999           | f32  | csst_ms_mbi_flux   | 

#### Header of `csst_ms_qc0 qc0 check`

| keyword  | value                 | comment                                        | fill value | type  | module      |
|----------|-----------------------|------------------------------------------------|------------|-------|-------------|
| VER_QC0  | '0.0.1'               | Pipeline version                               | '0.0.1'    | str   | csst_ms_qc0 |
| STA_QC0  | 0                     | QC0 Status (0/1/2)                             | -1         | int   | csst_ms_qc0 |
| STM_QC0  | '2022-12-30T18:36:05' | QC0 operation time                             | ---        | str   | csst_ms_qc0 |
| Q_CHKSUM | 0                     | CRC checksum                                   | 1          | int   | csst_ms_qc0 |
| F_TELSCP | 0                     | Telescope flag (0/bit)                         | ?          | int   | csst_ms_qc0 |
| Q_SHUTTR | 0                     | indicating shutter status                      | 1          | int   | csst_ms_qc0 |
| Q_COOLNG | 0                     | indicating system cooling status               | 1          | int   | csst_ms_qc0 |
| F_GUIDER | 0                     | Guider flag (0/bit)                            | ?          | int   | csst_ms_qc0 |
| Q_GUIDER | 0                     | indicating guiding stars status                | 1          | int   | csst_ms_qc0 |
| F_DETECT | 0                     | Detector flag (0/bit)                          | ?          | int   | csst_ms_qc0 |
| Q_DTDEAD | 0                     | indicating dead detector                       | 1          | int   | csst_ms_qc0 |
| Q_DTNOIS | 0                     | indicating higher detector noise level         | 1          | int   | csst_ms_qc0 |
| Q_DIFPAT | 0                     | indicating image diffraction pattern           | 1          | int   | csst_ms_qc0 |
| Q_XTALK  | 0                     | indicating significant image crosstalk         | 1          | int   | csst_ms_qc0 |
| Q_BADPIX | 0                     | CCD bad pixel fraction > 3 sigma               | 1          | int   | csst_ms_qc0 |
| Q_BRIBKG | 0                     | Significant stray light effect in this field   | 1          | int   | csst_ms_qc0 |
| Q_DTTEMP | 0                     | Large CCD temperature variation in this field  | 1          | int   | csst_ms_qc0 |

#### Header of `csst_ms_qc0 qc1 check`

| keyword | value                 | comment                  | fill value | type  | module         |
|---------|:----------------------|--------------------------|------------|-------|----------------|
| VER_QC1 | '0.0.1'               | Pipeline version         | '0.0.1'    | str   | csst_ms_qc0    |
| STA_QC1 | 0                     | QC1 Status (0/non-zero)  | -1         | int   | csst_ms_qc0    |
| STM_QC0 | '2022-12-30T18:36:05' | QC0 operation time       | ---        | str   | csst_ms_qc0    |
| Q_FOCUS | 0                     | focus status             | 1          | int   | csst_ms_qc0    |
| Q_WCS   | 0                     | WCS Calibration status   | 1          | int   | csst_ms_qc0    | 


## File: *_cat.fits

### File contents

| HDU  | data                    | note       |
|------|-------------------------|------------|
| HDU0 | None                    | PrimaryHDU |
| HDU1 | Table                   | ImageHDU   |

### HDU0

#### Header of photometry

| keyword            | value                             | comment                                     | fill value | type  | module                   |
|--------------------|:----------------------------------|---------------------------------------------|------------|-------|--------------------------|
| APERSIZE           | '3,4,5,6,8,10,13,16,20,25,30,40,' | aperture radii in pixels                    |  '3,4,5,6,8,10,13,16,20,25,30,40,'          | str   | csst_ms_mbi_photometry   |   
| NS_APER            | 75                                | number of stars used in aperture correction |   0         | i8    | csst_ms_mbi_photometry   | 
| APCOR0             | -0.06074262037873268              | mag correction for aperture #0              |   0.0         | f32   | csst_ms_mbi_photometry   |              
| APERR0             | 0.0                               | mag correction error for aperture #0        |   0.0         | f32   | csst_ms_mbi_photometry   |
| APCOR1             | -0.01975813694298267              | mag correction for aperture #1              |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR1             | 0.0                               | mag correction error for aperture #1        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR2             | 0.0                               | mag correction for aperture #2              |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR2             | 0.0                               | mag correction error for aperture #2        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR3             | 0.01290098764002323               | mag correction for aperture #3              |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR3             | 0.0                               | mag correction error for aperture #3        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR4             | 0.02804811112582684               | mag correction for aperture #4              |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR4             | 0.0                               | mag correction error for aperture #4        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR5             | 0.03705496713519096               | mag correction for aperture #5              |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR5             | 0.0                               | mag correction error for aperture #5        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR6             | 0.04462624341249466               | mag correction for aperture #6              |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR6             | 0.0                               | mag correction error for aperture #6        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR7             | 0.05059236660599709               | mag correction for aperture #7              |   0.0         | f32   | csst_ms_mbi_photometry   |            
| APERR7             | 0.0                               | mag correction error for aperture #7        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR8             | 0.05710481852293015               | mag correction for aperture #8              |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR8             | 0.0                               | mag correction error for aperture #8        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR9             | 0.06682745367288589               | mag correction for aperture #9              |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR9             | 0.0                               | mag correction error for aperture #9        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR10            | 0.07620415091514587               | mag correction for aperture #10             |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR10            | 0.0                               | mag correction error for aperture #10       |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APCOR11            | 0.0952027440071106                | mag correction for aperture #11             |   0.0         | f32   | csst_ms_mbi_photometry   |        
| APERR11            | 0.0                               | mag correction error for aperture #11       |   0.0         | f32   | csst_ms_mbi_photometry   |        
| NS_PSF             | 306                               | number of stars used in PSF correction      |   0         | i8    | csst_ms_mbi_photometry   |        
| PSFCOR             | -0.00268870708532631              | mag correction for PSF                      |   0.0         | f32   | csst_ms_mbi_photometry   |        
| PSFERR             | 0.000903990056504255              | mag correction error                        |   0.0         | f32   | csst_ms_mbi_photometry   |        
| NS_MODEL           | 324                               | number of stars used in MODEL correction    |   0         | i8    | csst_ms_mbi_photometry   |       
| MODCOR             | 0.04189466685056686               | mag correction for MODEL                    |   0.0         | f32   | csst_ms_mbi_photometry   |        
| MODERR             | 0.000894258863834524              | mag correction error                        |   0.0         | f32   | csst_ms_mbi_photometry   |        

### HDU1

#### Header

## File: *_psf.fits

### File contents

| HDU  | data                    | note       |
|------|-------------------------|------------|
| HDU0 | None                    | PrimaryHDU |
| HDU1 | Table                   | ImageHDU   |

### HDU0

#### Header

| keyword | value | comment        | fill value    | type | module           |
|---------|:------|----------------|---------------|------|------------------|
| SIMPLE  | True  | Fits standard  | True          | bool | csst_ooc_psf_mbi |  

### HDU1

#### Header of `csst_ooc_psf_mbi`

| keyword    | value        | comment                                       | fill value | type  | module             |
|------------|:-------------|-----------------------------------------------|------------|-------|--------------------|
| LOADED     | 579          | Number of loaded sources                      |   0         | I8    | csst_ooc_psf_mbi   |
| ACCEPTED   | 573          | Number of accepted sources                    |   0         | I8    | csst_ooc_psf_mbi   |
| CHI2       | 1.12832649   | Final reduced chi2                            |   0         | f32   | csst_ooc_psf_mbi   |
| POLNAXIS   | 2            | Number of context parameters                  |   0         | I8    | csst_ooc_psf_mbi   |
| POLGRP1    | 1            | Polynom group for this context parameter      |   0         | I8    | csst_ooc_psf_mbi   |
| POLNAME1   | 'XWIN_IMAGE' | Name of this context parameter                |   'XWIN_IMAGE'         | Str   | csst_ooc_psf_mbi   |
| POLZERO1   | 4607.403434  | Offset value for this context parameter       |   0         | f32   | csst_ooc_psf_mbi   |
| POLSCAL1   | 9161.359825  | Scale value for this context parameter        |   0         | f32   | csst_ooc_psf_mbi   |
| POLGRP2    | 1            | Polynom group for this context parameter      |   1         | I8    | csst_ooc_psf_mbi   |
| POLNAME2   | 'YWIN_IMAGE' | Name of this context parameter                |  'YWIN_IMAGE'          | Str   | csst_ooc_psf_mbi   |
| POLZERO2   | 4631.62895   | Offset value for this context parameter       |   0         | f32   | csst_ooc_psf_mbi   |
| POLSCAL2   | 9174.347872  | Scale value for this context parameter        |   0         | f32   | csst_ooc_psf_mbi   |
| POLNGRP    | 1            | Number of context groups                      |   1         | I8    | csst_ooc_psf_mbi   |
| POLDEG1    | 2            | Polynom degree for this context group         |   2         | I8    | csst_ooc_psf_mbi   |
| PSF_FWHM   | 2.31607056   | PSF FWHM in image pixels                      |   0         | f32   | csst_ooc_psf_mbi   |
| PSF_SAMP   | 0.49278098   | Sampling step of the PSF data in image pixels |   0         | f32   | csst_ooc_psf_mbi   |
| PSFNAXIS   | 3            | Dimensionality of the PSF data                |   0         | I8    | csst_ooc_psf_mbi   |
| PSFAXIS1   | 71           | Number of element along this axis             |   0         | I8    | csst_ooc_psf_mbi   |
| PSFAXIS2   | 71           | Number of element along this axis             |   0         | I8    | csst_ooc_psf_mbi   |
| PSFAXIS3   | 6            | Number of element along this axis             |   0         | I8    | csst_ooc_psf_mbi   |

#### Header of `csst_ooc_psf_strategy_crds`

| keyword    | value                 | comment                                                                                                                                | fill value | type   | module                       |
|------------|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------|------------|--------|------------------------------|
| USEAFTER   | '2028-07-22T18:52:33' | date and time after the reference files will be used. (YYYY-MM-DDThh:mm:ss)                                                            |            | str    | csst_ooc_psf_strategy_crds   |
| OBSSTART   | '2028-07-22T18:52:33' | UTC date and time of start of first observation (YYYY-MM-DDThh:mm:ss)                                                                  |            | str    | csst_ooc_psf_strategy_crds   |
| OBSEND     | '2028-07-23T17:54:27' | UTC date and time of end of last observation (YYYY-MM-DDThh:mm:ss)                                                                     |            | str    | csst_ooc_psf_strategy_crds   |
| EXPTYPE    | 'SCI'                 | type of exposes used to create the reference file ('SCI'or 'OOC')                                                                      |            | str    | csst_ooc_psf_strategy_crds   |
| COMBINE_N  | 135                   | number of exposes used to create the reference file.                                                                                   |            | I8     | csst_ooc_psf_strategy_crds   |
| BREAPHAS   | 'hot'                 | phase of breathing effect, which is the focus varies over orbital time <br> scales due to thermal changes. ('hot', 'cold'. 'none')     |            | str    | csst_ooc_psf_strategy_crds   |
| TEMP_PM    | 20.72563452           | average temperature surrounding the primary mirror (in K)                                                                              |            | f32    | csst_ooc_psf_strategy_crds   |
| TEMP_SM    | 20.72563452           | average temperature surrounding the secondary mirror (in K)                                                                            |            | f32    | csst_ooc_psf_strategy_crds   |
| TEMP_TM    | 20.72563452           | average temperature surrounding the tertiary mirror (in K)                                                                             |            | f32    | csst_ooc_psf_strategy_crds   |
| LFOCUST    | '2028-07-22T18:52:33' | last focus (AM1 or AM2) time (YYYY-MM-DDThh:mm:ss)                                                                                     |            | str    | csst_ooc_psf_strategy_crds   |
| P1_FOCUS   | 28025.63452           | parameter 1 of focal length calculated from the positions ofthe focus <br> adjustment mechanism (FAM) and the secondary mirror (in mm) |            | f32    | csst_ooc_psf_strategy_crds   |
| P2_ FOCUS  | 28025.63452           | parameter 2 of focal length (in mm)                                                                                                    |            | f32    | csst_ooc_psf_strategy_crds   |
| P3_ FOCUS  | 28025.63452           | parameter 3 of focal length (in mm)                                                                                                    |            | f32    | csst_ooc_psf_strategy_crds   |
| P4_ FOCUS  | 28025.63452           | parameter 4 of focal length (in mm)                                                                                                    |            | f32    | csst_ooc_psf_strategy_crds   |
| P5_ FOCUS  | 28025.63452           | parameter 5 of focal length (in mm)                                                                                                    |            | f32    | csst_ooc_psf_strategy_crds   |
| P6_ FOCUS  | 28025.63452           | parameter 6 of focal length (in mm)                                                                                                    |            | f32    | csst_ooc_psf_strategy_crds   |
| FSM_STAT   | T                     | working state of fast-steering mirror (FSM)                                                                                            |            | bool   | csst_ooc_psf_strategy_crds   |


#### Header of `csst_ms_mbi_astrometry`

| keyword   | value                     | comment                       | fallback_value | type | module                  |
|-----------|:--------------------------|-------------------------------|----------------|------|-------------------------|
| STA_CCRS  |  0                        |  Completion degree of relative astrometric solution in CCRS       | 1                     | i8  |csst_ms_mbi_astrometry  |
| VER_CCRS  |  "v2023.01"               |  Version of CSST relative Astrometry soft in CCRS                 | "v2023.01"            | str |csst_ms_mbi_astrometry  |
| CCRSGATE  |  "  "                     |  Camera shutter information                                       | "   "                 | str |csst_ms_mbi_astrometry  |
| CCRSCONF  |  "  "                     |  Configuration file for astrometry                                | "   "                 | str |csst_ms_mbi_astrometry  |
| CCRSIM    |  " normal"                |  Image classification for CSST Astrometry                         | " normal "            | str |csst_ms_mbi_astrometry  |
| CCRSTM    |  2023:02:03-12:03:04      |  Time of last CSST Astrometry in CCRS                             | 2023:02:03-12:03:04   | str |csst_ms_mbi_astrometry  |
| CCRSREF   |  "Gaia dr3 v01"           |  Reference Catalogue for CSST Astrometry in CCRS                  | "Gaia dr3 v01"        | str |csst_ms_mbi_astrometry  |
| CCRSHIS   |  1                        |  Astrometric solution Record for CCRS                             | 1                     | i8  |csst_ms_mbi_astrometry  |
| DELT_RA   |  0.3                      |  Change in central RA                                             | 0                     | f32 |csst_ms_mbi_astrometry  |
| DELT_dec  |  0.3                      |  Change in central DEC                                            | 0                     | f32 |csst_ms_mbi_astrometry  |
| DELT_ps   |  0.3                      |  Change in pixelscale                                             | 0                     | f32 |csst_ms_mbi_astrometry  |
| CCDALCE   |  3468                     |  CCD Centroid   along  coordinate for CCRS                        | -9999                  | f32 |csst_ms_mbi_astrometry  |
| CCDALCEE  |  3                        |  CCD Centroid   along coordinate Error for CCRS                   | -9999                  | f32 |csst_ms_mbi_astrometry  |
| CCDACCE   |  3468                     |  CCD Centroid   along  coordinate for CCRS                        | -9999                  | f32 |csst_ms_mbi_astrometry  |
| CCDACCEE  |  3                        |  CCD Centroid   across  coordinate Error for CCRS                 | -9999                  | f32 |csst_ms_mbi_astrometry  |
| CCD_ROW   |  2                        |  CCD Row for CCRS                                                 | 2                     | i8  |csst_ms_mbi_astrometry  |
| CCD_COL   |  2                        |  CCD Column for CCRS                                              | 2                     | i8  |csst_ms_mbi_astrometry  |
| EQUINOX   |  2000                     |  Reference epoch for CCRS                                         | 2000                  | f32 |csst_ms_mbi_astrometry  |
| RADESYS   |  "CCRS"                   |  Reference coordinate system for CCRS                             | "CCRS"                | str |csst_ms_mbi_astrometry  |
| CTYPE1    |  'RA---TPV'               |  WCS projection type for this axis                                | 'RA---TPV'            | str |csst_ms_mbi_astrometry  |
| CTYPE2    |  'DEC--TPV'               |  WCS projection type for this axis                                | 'DEC--TPV'            | str |csst_ms_mbi_astrometry  |
| CUNIT1    |  'deg     '               |  Axis unit                                                        | 'deg     '            | str |csst_ms_mbi_astrometry  |
| CUNIT2    |  'deg     '               |  Axis unit                                                        | 'deg     '            | str |csst_ms_mbi_astrometry  |
| CRVAL1    |  9.030599852245E+01       |  World coordinate on this axis                                    | Read from level 0 data| f32 |csst_ms_mbi_astrometry  |
| CRVAL2    |  2.438488373039E+01       |  World coordinate on this axis                                    | Read from level 0 data| f32 |csst_ms_mbi_astrometry  |
| CRPIX1    |  4.694923673820E+03       |  Reference pixel on this axis                                     | Read from level 0 data| f32 |csst_ms_mbi_astrometry  |
| CRPIX2    |  4.619541250822E+03       |  Reference pixel on this axis                                     | Read from level 0 data| f32 |csst_ms_mbi_astrometry  |
| CD1_1     |  -8.151272405944E-06      | Linear projection matrix                                          | Read from level 0 data| f32 |csst_ms_mbi_astrometry  |
| CD1_2     |  -1.872449650544E-05      | Linear projection matrix                                          | Read from level 0 data| f32 |csst_ms_mbi_astrometry  |
| CD2_1     |  1.876564643792E-05       | Linear projection matrix                                          | Read from level 0 data| f32 |csst_ms_mbi_astrometry  |
| CD2_2     |  -8.133840508591E-06      | Linear projection matrix                                          | Read from level 0 data| f32 |csst_ms_mbi_astrometry  |
| PV1_0     |   5.170560041120E-06      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_1     |   9.998597063949E-01      | Projection distortion parameter               | 1 | f32 |csst_ms_mbi_astrometry  |
| PV1_2     |  -2.639332324050E-05      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_4     |  -2.036180144002E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_5     |  -9.700979957371E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_6     |   2.985621009586E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_7     |   1.352911042189E-02      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_8     |  -2.059801280272E-02      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_9     |   1.720680837477E-02      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_10    |   9.773972553669E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_12    |  -1.447093954841E-01      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_13    |   3.877149836968E-01      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_14    |  -5.851518938865E-01      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_15    |   3.482309631134E-01      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV1_16    |  -2.183057017500E-01      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_0     |   1.728529121022E-05      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_1     |   9.999804628736E-01      | Projection distortion parameter               | 1 | f32 |csst_ms_mbi_astrometry  |
| PV2_2     |  -6.335240164790E-05      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_4     |  -5.966442744430E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_5     |   6.203002956354E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_6     |  -3.553022699090E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_7     |  -3.813262941731E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_8     |   5.844942621588E-02      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_9     |   4.675092996504E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_10    |  -7.886221100639E-03      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_12    |   3.250659874395E-01      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_13    |  -4.054835390976E-01      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_14    |   7.550500477228E-01      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_15    |  -2.401706541249E-02      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| PV2_16    |   3.205340695247E-01      | Projection distortion parameter               | 0 | f32 |csst_ms_mbi_astrometry  |
| ASTIRMS1  | 0.000000000000E+00        | Astrom. dispersion RMS (intern., high S/N)    | -9999       | f32  | csst_ms_mbi_astrometry  |
| ASTIRMS1  | 0.000000000000E+00        | Astrom. dispersion RMS (intern., high S/N)    | -9999       | f32  | csst_ms_mbi_astrometry  |
| ASTIRMS1  | 6.458653303335E-06        | Astrom. dispersion RMS (ref., high S/N)       | -9999       | f32  | csst_ms_mbi_astrometry  |
| ASTIRMS1  | 8.724734011714E-06        | Astrom. dispersion RMS (ref., high S/N)       | -9999       | f32  | csst_ms_mbi_astrometry  |

