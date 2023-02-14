# L1-MBI Data model

## File: *_{img/wht/flg}_L1_1.fits

### File contents
| HDU  | data                    | note       |
|------|-------------------------|------------|
| HDU0 | None                    | PrimaryHDU |
| HDU1 | reduced image (9k x 9k) | ImageHDU   |


### HDU0
| keyword | value | comment       | fallback_value | type | module    |
|---------|:------|---------------|----------------|------|-----------|
| SIMPLE  | True  | Fits standard | True           | bool | csst_sims |     

### HDU1

#### Header of `csst_ms_mbi_instrument`
| keyword   | value                     | comment                       | fallback_value | type | module                  |
|-----------|:--------------------------|-------------------------------|----------------|------|-------------------------|
|SATURATE   | 1833.333333333333         |                                                |                | f32  | csst_ms_mbi_instrument   |         
|CRCOUNT    | 66791                     |                                                |                | i8   | csst_ms_mbi_instrument   |
|INST_V     | '0.0.1   '                |                                                |                | str  | csst_ms_mbi_instrument   |
|INST_TOL   | '2022-12-30T10:18:53'     | Time of last modification                      |                | str  | csst_ms_mbi_instrument   |
|DATASUM    | '1352015684'              | data unit checksum updated 2022-10-28T19:29:10 |                | str  | csst_ms_mbi_instrument   |

#### Header of `csst_ms_mbi_distortion`

| keyword   | value                     | comment                       | fallback_value | type | module                  |
|-----------|:--------------------------|-------------------------------|----------------|------|-------------------------|
| RADESYS   | 'ICRS    '                | should be always 'ICRS'       | 'ICRS'                | str  | csst_ms_mbi_distortion  |                             
| STAR_FIT  | 11                        |                               | 0                     | i8   | csst_ms_mbi_distortion  | 
| PV1_0     | 0.003205383944913964      |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV1_1     | 0.8673020820536499        |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV1_2     | -0.2011989871377834       |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV1_3     | -0.2597214229472611       |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV1_4     | 0.4353828741811097        |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV1_5     | -0.5054216569802673       |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV1_6     | 0.1951474426617432        |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV2_0     | 0.00109803885992697       |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV2_1     | 0.9171065857705857        |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV2_2     | -0.04908256792722099      |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV2_3     | -0.09860562038448289      |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV2_4     | 0.07961855240788976       |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV2_5     | -0.2009224365497067       |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| PV2_6     | 0.1741954691884874        |                               | 0                     | f32  | csst_ms_mbi_distortion  |
| RA_OFF    | -0.0                      | mas in unit                   | -99                   | f32  | csst_ms_mbi_distortion  |
| DEC_OFF   | 0.0                       | mas in unit                   | -99                   | f32  | csst_ms_mbi_distortion  |
| RA_STD    | 127.1                     | mas in unit                   | -99                   | f32  | csst_ms_mbi_distortion  |
| DEC_STD   | 60.4                      | mas in unit                   | -99                   | f32  | csst_ms_mbi_distortion  |
| RA_CEN    | 192.1940713422841         | the center of detector in ra  | 192.1940713422841     | f32  | csst_ms_mbi_distortion  |
| DEC_CEN   | 26.72643742371229         | the center of detector in dec | 26.72643742371229     | f32  | csst_ms_mbi_distortion  |
| DIST_V    | '1.0     '                | version of distortion         | '1.0'                 | str  | csst_ms_mbi_distortion  |
| DIST_TOL  | '2022-12-29T16:36:47'     | distortion operation time     | '2022-12-29T16:36:47' | str  | csst_ms_mbi_distortion  |
| DIST_S    |                   0       | 0=done 1=wrong                | 1                     | i8   | csst_ms_mbi_distortion  | 

#### Header of `csst_ms_mbi_position`

| keyword   | value                     | comment                       | fallback_value | type | module                  |
|-----------|:--------------------------|-------------------------------|----------------|------|-------------------------|
| RADESYS   | 'ICRS    '                | should be always 'ICRS'       | 'ICRS'                | str  | csst_ms_mbi_position  |                             
| PV1_0     | -7.032303876526E-04       |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV1_1     | 9.986639936274E-01        |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV1_2     | -3.506141592607E-03       |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV1_4     | -2.342575913122E-03       |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV1_5     | -2.216829433925E-03       |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV1_6     | -5.122207406521E-03       |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV2_0     | -6.939462894407E-04       |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV2_1     | 9.988294486003E-01        |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV2_2     | -1.687802061938E-03       |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV2_4     | 1.561587727533E-03        |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV2_5     | -4.159618376671E-03       |                               | 0                     | f32  | csst_ms_mbi_position  |
| PV2_6     | 3.398895060382E-03        |                               | 0                     | f32  | csst_ms_mbi_position  |
| FGROUPNO  |                   1       | SCAMP field group label       |                       | i8   | csst_ms_mbi_position  |
| ASTIRMS1  | 0.000000000000E+00        | Astrom. dispersion RMS (intern., high S/N) |          | f32  | csst_ms_mbi_position  |    
| ASTIRMS2  | 0.000000000000E+00        | Astrom. dispersion RMS (intern., high S/N) |          | f32  | csst_ms_mbi_position  |
| ASTRRMS1  | 6.458653303335E-06        | Astrom. dispersion RMS (ref., high S/N)    |          | f32  | csst_ms_mbi_position  |
| ASTRRMS2  | 8.724734011714E-06        | Astrom. dispersion RMS (ref., high S/N)    |          | f32  | csst_ms_mbi_position  |       
| ASTINST   |                   1       | SCAMP astrometric instrument label         |          | i8   | csst_ms_mbi_position  |
| FLXSCALE  | 1.000000000000E+00        | SCAMP relative flux scale                  |          | f32  | csst_ms_mbi_position  |                     
| MAGZEROP  |          0.00000000       | SCAMP zero-point                           |          | f32  | csst_ms_mbi_position  |                               
| PHOTIRMS  |          0.00000000       | mag dispersion RMS (internal, high S/N)    |          | f32  | csst_ms_mbi_position  |
| PHOTINST  |                   1       | SCAMP photometric instrument label         |          | i8   | csst_ms_mbi_position  |
| PHOTLINK  |                   F       | True if linked to a photometric field      |          | bool | csst_ms_mbi_position  |
| WCS_S     |                   0       | 0=done                                     |          | i8   | csst_ms_mbi_position  | 
| WCS_V     | '2.0.4   '                | Version of WCS calibration                 |          | str  | csst_ms_mbi_position  |        
| WCS_P     | 'default.scamp'           | Configure file name of WCS                 |          | str  | csst_ms_mbi_position  |                    
| WCS_TOL   | '2022-12-30 18:32:46 PM'  | Time of last wcs calibration               |          | str  | csst_ms_mbi_position  |             

#### Header of `csst_ms_mbi_flux`

| keyword   | value                     | comment                       | fallback_value | type | module                  |
|-----------|:--------------------------|-------------------------------|----------------|------|-------------------------|
| CALI_REF  | 'GAIA    '                | the reference database for calibration        |     | str  | csst_ms_mbi_flux   |
| ZP        |             23.8435       | photometric zero point in magnitude           |     | f32  | csst_ms_mbi_flux   |
| ZPRMS     |             0.0101        | zpt rms of the matched objects                |     | f32  | csst_ms_mbi_flux   |                
| APER_R    |                 10        | (pixels) photo-aperture radius                |     | i8   | csst_ms_mbi_flux   |            
| FWHM      |                2.147      | FWHM in pixel                                 |     | f32  | csst_ms_mbi_flux   |
| RAOFF     |             -0.188        | median positional offset from GAIA, in arcsec |     | f32  | csst_ms_mbi_flux   |
| DECOFF    |            -0.1061        | median positional offset from GAIA, in arcsec |     | f32  | csst_ms_mbi_flux   | 
| NSTAR     |                 49        | total number of stars detected                |     | i8   | csst_ms_mbi_flux   | 
| NMATCH    |                 25        | total number of matched stars in 2 arcsec     |     | i8   | csst_ms_mbi_flux   |
| MDNCOL    |                0.0        | median (BP-RP)_GAIA of matched stars          |     | f32  | csst_ms_mbi_flux   |
| SKY       |             0.0359        | (e-/s per pixel)                              |     | f32  | csst_ms_mbi_flux   |                 
| SKYRMS    |             0.1766        | rms/pixel of the sky in unit of e-/s          |     | f32  | csst_ms_mbi_flux   | 
| MLIM      |              21.83        | magnitude limiting of 5-sigma galaxy detection|     | f32  | csst_ms_mbi_flux   | 
| FLUX_S    |                  0        | flux calibration status                       |     | i8   | csst_ms_mbi_flux   |                       
| FLUX_V    |  '1.3     '               | version of calibration code                   |     | str  | csst_ms_mbi_flux   |
| FLUX_TOL= |  '2022-12-30 18:36:05'    | flux calibration operation time               |     | str  | csst_ms_mbi_flux   |

#### Header of `csst_ms_qc0 qc0 check`
| keyword    | value                     | comment                                        | fallback_value        | type | module                  |
|------------|--------------------------|------------------------------------------------|-----------------------|------|-------------------------|
| CRCCHECK | T | CRC validation | F | bool | csst_ms_qc0 |
| PRIPARAM | 0 | Primary parameters verification | 1 | int| csst_ms_qc0 |
| SECPARAM | 0 | Secondary parameters verification | 1 | int | csst_ms_qc0 |
| QC0_S | 0 | QC0 Status (0/non-zero) | > 0 | int | csst_ms_qc0 |
| DATAERR | F | indicating data error | T | bool | csst_ms_qc0 |
| IMGERR | F | indicating image error  | T | bool | csst_ms_qc0 |
| SHUTTER | F | indicating shutter error | T | bool | csst_ms_qc0 
| FAILGUID | F | missing guiding stars | T | bool | csst_ms_qc0 |
| FAILCOOL | F | indicating system cooling error | T | bool | csst_ms_qc0 |
| GUID_OFF | 0.0 | guiding stars offset (arcsec) | -9999 | f32 | csst_ms_qc0 |
| DEAD_CCD | F | indicating dead CCD | T | bool | csst_ms_qc0 |
| NOIS_CCD | F | indicating higher CCD noise level | T | bool | csst_ms_qc0 |
| FF_PETAL | F | indicating image diffraction pattern | T | bool | csst_ms_qc0 |
| GUID_ERR | F | indicating larger guiding offset | T | bool | csst_ms_qc0 |
| CROSTALK | F | indicating significant image crosstalk | T | bool | csst_ms_qc0 |
| BADPIXFR | 0.0 | CCD bad pixel fraction (unitless) | -9999 | f32 | csst_ms_qc0 |
| PSF_SIZE | 0.0 | Best-fit PSF size from guider | -9999 | f32 | csst_ms_qc0 |
| STRLIGHT | F | Significant stray light effect in this field | T | bool | csst_ms_qc0 |
| BAD_ROT | F | indicating bad rotation effect in this field | T | bool | csst_ms_qc0 |
| BRI_STAR | F | Significant bright star in this field | T | bool | csst_ms_qc0 |
| CCD_TEMP | 0.0 | Large CCD temperature variation in this field | -9999 | f32 | csst_ms_qc0 |
| VER_QC0 | '0.0.1' | Pipeline version | '0.0.1' | str | csst_ms_qc0 | 




## File: *_cat.fits

### File contents
| HDU  | data                    | note       |
|------|-------------------------|------------|
| HDU0 | None                    | PrimaryHDU |
| HDU1 | Table                   | ImageHDU   |

### HDU0

#### Header of photometry
| keyword   | value                     | comment                       | fallback_value | type | module                  |
|-----------|:--------------------------|-------------------------------|----------------|------|-------------------------|
| APERSIZE  | '3,4,5,6,8,10,13,16,20,25,30,40,' | aperture radii in pixels  |            | str  |  csst_ms_mbi_photometry |   
| NS_APER   |            75 | number of stars used in aperture correction   |            | i8   |  csst_ms_mbi_photometry | 
| APCOR0    | -0.06074262037873268 | mag correction for aperture #0         |            | f32  |  csst_ms_mbi_photometry |              
| APERR0    |                0.0   | mag correction error for aperture #0   |            | f32  |  csst_ms_mbi_photometry |
| APCOR1    | -0.01975813694298267 | mag correction for aperture #1         |            | f32  |  csst_ms_mbi_photometry |        
| APERR1    |                 0.0  | mag correction error for aperture #1   |            | f32  |  csst_ms_mbi_photometry |        
| APCOR2    |                 0.0  | mag correction for aperture #2         |            | f32  |  csst_ms_mbi_photometry |        
| APERR2    |                 0.0  | mag correction error for aperture #2   |            | f32  |  csst_ms_mbi_photometry |        
| APCOR3    | 0.01290098764002323  | mag correction for aperture #3         |            | f32  |  csst_ms_mbi_photometry |        
| APERR3    |                 0.0  | mag correction error for aperture #3   |            | f32  |  csst_ms_mbi_photometry |        
| APCOR4    | 0.02804811112582684  | mag correction for aperture #4         |            | f32  |  csst_ms_mbi_photometry |        
| APERR4    |                 0.0  | mag correction error for aperture #4   |            | f32  |  csst_ms_mbi_photometry |        
| APCOR5    | 0.03705496713519096  | mag correction for aperture #5         |            | f32  |  csst_ms_mbi_photometry |        
| APERR5    |                 0.0  | mag correction error for aperture #5   |            | f32  |  csst_ms_mbi_photometry |        
| APCOR6    | 0.04462624341249466  | mag correction for aperture #6         |            | f32  |  csst_ms_mbi_photometry |        
| APERR6    |                 0.0  | mag correction error for aperture #6   |            | f32  |  csst_ms_mbi_photometry |        
| APCOR7    | 0.05059236660599709  | mag correction for aperture #7         |            | f32  |  csst_ms_mbi_photometry |            
| APERR7    |                 0.0  | mag correction error for aperture #7   |            | f32  |  csst_ms_mbi_photometry |        
| APCOR8    |  0.05710481852293015 | mag correction for aperture #8         |            | f32  |  csst_ms_mbi_photometry |        
| APERR8    |                  0.0 | mag correction error for aperture #8   |            | f32  |  csst_ms_mbi_photometry |        
| APCOR9    |  0.06682745367288589 | mag correction for aperture #9         |            | f32  |  csst_ms_mbi_photometry |        
| APERR9    |                  0.0 | mag correction error for aperture #9   |            | f32  |  csst_ms_mbi_photometry |        
| APCOR10   |  0.07620415091514587 | mag correction for aperture #10        |            | f32  |  csst_ms_mbi_photometry |        
| APERR10   |                  0.0 | mag correction error for aperture #10  |            | f32  |  csst_ms_mbi_photometry |        
| APCOR11   |   0.0952027440071106 | mag correction for aperture #11        |            | f32  |  csst_ms_mbi_photometry |        
| APERR11   |                  0.0 | mag correction error for aperture #11  |            | f32  |  csst_ms_mbi_photometry |        
| HIERARCH ns_HYBRID | 328 |number of stars used in HYBRID correction       |            | i8   |  csst_ms_mbi_photometry |          
| HYBCOR    |  0.0498337559401989  | mag correction for HYBRID              |            | f32  |  csst_ms_mbi_photometry |        
| HYBERR    | 0.000711286964798456 | mag correction error                   |            | f32  |  csst_ms_mbi_photometry |        
| NS_PSF    |                  306 | number of stars used in PSF correction |            | i8   |  csst_ms_mbi_photometry |        
| PSFCOR    | -0.00268870708532631 | mag correction for PSF                 |            | f32  |  csst_ms_mbi_photometry |        
| PSFERR    | 0.000903990056504255 | mag correction error                   |            | f32  |  csst_ms_mbi_photometry |        
| NS_MODEL  |                  324 | number of stars used in MODEL correction|            | i8  |  csst_ms_mbi_photometry |       
| MODCOR    |  0.04189466685056686 | mag correction for MODEL               |            | f32  |  csst_ms_mbi_photometry |        
| MODERR    |  0.000894258863834524| mag correction error                   |            | f32  |  csst_ms_mbi_photometry |        

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

| keyword | value | comment       | fallback_value | type | module           |
|---------|:------|---------------|----------------|------|------------------|
| SIMPLE  | True  | Fits standard | True           | bool | csst_ooc_psf_mbi |  

### HDU1

#### Header of `csst_ooc_psf_mbi`

| keyword  | value        | comment                                       | fallback_value | type | module           |
| -------- |:------------ | --------------------------------------------- | -------------- | ---- | ---------------- |
| LOADED   | 579          | Number of loaded sources                      |                | I8   | csst_ooc_psf_mbi |
| ACCEPTED | 573          | Number of accepted sources                    |                | I8   | csst_ooc_psf_mbi |
| CHI2     | 1.12832649   | Final reduced chi2                            |                | f32  | csst_ooc_psf_mbi |
| POLNAXIS | 2            | Number of context parameters                  |                | I8   | csst_ooc_psf_mbi |
| POLGRP1  | 1            | Polynom group for this context parameter      |                | I8   | csst_ooc_psf_mbi |
| POLNAME1 | 'XWIN_IMAGE' | Name of this context parameter                |                | Str  | csst_ooc_psf_mbi |
| POLZERO1 | 4607.403434  | Offset value for this context parameter       |                | f32  | csst_ooc_psf_mbi |
| POLSCAL1 | 9161.359825  | Scale value for this context parameter        |                | f32  | csst_ooc_psf_mbi |
| POLGRP2  | 1            | Polynom group for this context parameter      |                | I8   | csst_ooc_psf_mbi |
| POLNAME2 | 'YWIN_IMAGE' | Name of this context parameter                |                | Str  | csst_ooc_psf_mbi |
| POLZERO2 | 4631.62895   | Offset value for this context parameter       |                | f32  | csst_ooc_psf_mbi |
| POLSCAL2 | 9174.347872  | Scale value for this context parameter        |                | f32  | csst_ooc_psf_mbi |
| POLNGRP  | 1            | Number of context groups                      |                | I8   | csst_ooc_psf_mbi |
| POLDEG1  | 2            | Polynom degree for this context group         |                | I8   | csst_ooc_psf_mbi |
| PSF_FWHM | 2.31607056   | PSF FWHM in image pixels                      |                | f32  | csst_ooc_psf_mbi |
| PSF_SAMP | 0.49278098   | Sampling step of the PSF data in image pixels |                | f32  | csst_ooc_psf_mbi |
| PSFNAXIS | 3            | Dimensionality of the PSF data                |                | I8   | csst_ooc_psf_mbi |
| PSFAXIS1 | 71           | Number of element along this axis             |                | I8   | csst_ooc_psf_mbi |
| PSFAXIS2 | 71           | Number of element along this axis             |                | I8   | csst_ooc_psf_mbi |
| PSFAXIS3 | 6            | Number of element along this axis             |                | I8   | csst_ooc_psf_mbi |

#### Header of `csst_ooc_psf_strategy_crds`

| keyword   | value                 | comment                                                                                                                                | fallback_value | type | module                     |
| --------- | --------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------- | ---- | -------------------------- |
| USEAFTER  | '2028-07-22T18:52:33' | date and time after the reference files will be used. (YYYY-MM-DDThh:mm:ss)                                                            |                | str  | csst_ooc_psf_strategy_crds |
| OBSSTART  | '2028-07-22T18:52:33' | UTC date and time of start of first observation (YYYY-MM-DDThh:mm:ss)                                                                  |                | str  | csst_ooc_psf_strategy_crds |
| OBSEND    | '2028-07-23T17:54:27' | UTC date and time of end of last observation (YYYY-MM-DDThh:mm:ss)                                                                     |                | str  | csst_ooc_psf_strategy_crds |
| EXPTYPE   | 'SCI'                 | type of exposes used to create the reference file ('SCI'or 'OOC')                                                                      |                | str  | csst_ooc_psf_strategy_crds |
| COMBINE_N | 135                   | number of exposes used to create the reference file.                                                                                   |                | I8   | csst_ooc_psf_strategy_crds |
| BREAPHAS  | 'hot'                 | phase of breathing effect, which is the focus varies over orbital time <br> scales due to thermal changes. ('hot', 'cold'. 'none')     |                | str  | csst_ooc_psf_strategy_crds |
| TEMP_PM   | 20.72563452           | average temperature surrounding the primary mirror (in K)                                                                              |                | f32  | csst_ooc_psf_strategy_crds |
| TEMP_SM   | 20.72563452           | average temperature surrounding the secondary mirror (in K)                                                                            |                | f32  | csst_ooc_psf_strategy_crds |
| TEMP_TM   | 20.72563452           | average temperature surrounding the tertiary mirror (in K)                                                                             |                | f32  | csst_ooc_psf_strategy_crds |
| LFOCUST   | '2028-07-22T18:52:33' | last focus (AM1 or AM2) time (YYYY-MM-DDThh:mm:ss)                                                                                     |                | str  | csst_ooc_psf_strategy_crds |
| P1_FOCUS  | 28025.63452           | parameter 1 of focal length calculated from the positions ofthe focus <br> adjustment mechanism (FAM) and the secondary mirror (in mm) |                | f32  | csst_ooc_psf_strategy_crds |
| P2_ FOCUS | 28025.63452           | parameter 2 of focal length (in mm)                                                                                                    |                | f32  | csst_ooc_psf_strategy_crds |
| P3_ FOCUS | 28025.63452           | parameter 3 of focal length (in mm)                                                                                                    |                | f32  | csst_ooc_psf_strategy_crds |
| P4_ FOCUS | 28025.63452           | parameter 4 of focal length (in mm)                                                                                                    |                | f32  | csst_ooc_psf_strategy_crds |
| P5_ FOCUS | 28025.63452           | parameter 5 of focal length (in mm)                                                                                                    |                | f32  | csst_ooc_psf_strategy_crds |
| P6_ FOCUS | 28025.63452           | parameter 6 of focal length (in mm)                                                                                                    |                | f32  | csst_ooc_psf_strategy_crds |
| FSM_STAT  | T                     | working state of fast-steering mirror (FSM)                                                                                            |                | bool | csst_ooc_psf_strategy_crds |
