# L1-MBI Data model

## File: \*\_*_L1_1.fits

### File contents

| HDU   | data                    | note        |
|-------|-------------------------|-------------|
| HDU0  | None                    | PrimaryHDU  |
| HDU1  | reduced SCI (9k x 9k)   | ImageHDU    |
| HDU2  | reduced ERR (9k x 9k)   | ImageHDU    |
| HDU3  | reduced DQ (9k x 9k)    | ImageHDU    |

- 关键字 comment大写开头
- 

### *HDU0 --> HDU1

HDU0 修改 `NEXTEND=3`
模块之间用COMMENT隔开，例如
```
COMMENT ==================================================================      
COMMENT QC0 CHECK                                                               
COMMENT ==================================================================  
```
精简每个关键字的comment
`-`表示不可能失败，不会使用fallback_value


### HDU1-1 (先不管)

| keyword            | value                  | comment                                       | fallback_value        | type   | module                  |
|--------------------|:-----------------------|-----------------------------------------------|-----------------------|--------|-------------------------|
| VER_CRDS           | '0.0.1 '               | Version of CRDS file selection software used  | -                     | str    | csst_ms_sls_instrument  |
| R_GAIN             | '*.gain.fits'          | Gain reference file name                      | 'N/A'                 | str    | csst_ms_sls_instrument  |
| R_READN            | '*.rn.fits'            | Read noise reference file name                | 'N/A'                 | str    | csst_ms_sls_instrument  |
| R_SATURA           | '*.sat.fits'           | Saturation reference file name                | 'N/A'                 | str    | csst_ms_sls_instrument  |
| R_MASK             | '*.msk.fits'           | Mask reference file name                      | 'N/A'                 | str    | csst_ms_sls_instrument  |
| R_BIAS             | '*bias.fits'           | SuperBias reference file name                 | 'N/A'                 | str    | csst_ms_sls_instrument  |
| R_DARK             | '*dark.fits'           | Dark reference file name                      | 'N/A'                 | str    | csst_ms_sls_instrument  |
| R_DFLAT            | '*flat.fits'           | Detector Flat reference file name             | 'N/A'                 | str    | csst_ms_sls_instrument  |
| R_SFLAT            | '*flat.fits'           | Spectrograph Flat reference file name         | 'N/A'                 | str    | csst_ms_sls_instrument  |
| S_DQINI            | 1                     | Data Quality Initialization                   | 0                     | int  | csst_ms_sls_instrument  |
| S_SATURA           | 1                      | Saturation Checking                           | 0                     | int   | csst_ms_sls_instrument  |
| S_ERRINI           | 1                      | Error Initialization                          | 0                     | int   | csst_ms_sls_instrument  |
| S_BIAS             | 1                      | Bias correction                               | 0                     | int   | csst_ms_sls_instrument  |
| S_DARK             | 1                     | Dark correction                               | 0                     | int   | csst_ms_sls_instrument  |
| S_FLAT             | 1                      | Flat field correction                         | 0                     | int   | csst_ms_sls_instrument  |
| VER_INST           | '0.0.1 '               | Instrument calibration pipeline version   | -                     | str    | csst_ms_sls_instrument  |
| STM_INST | '2022-12-30T10:18:53'  | Instrument pipeline processing time                      | '2022-12-30T10:18:53' | str    | csst_ms_sls_instrument  |
| HISTORY            | '**step complete.'     | Record processing message                     | -              | str    | csst_ms_sls_instrument  |

### HDU1

#### Header of `csst_ms_sls_instrument`

`IMAGE STATISTICS AND DATA QUALITY FLAGS` 需要修改成为标准格式，首字母大写
增加宇宙线证认相关关键字

| keyword   | value    | comment                                 | fallback_value | type | module                   |
|-----------|:---------|-----------------------------------------|----------------|------|--------------------------|
| EXTNAME   | SCI      | Extension name                          | SCI            | str  | csst_ms_sls_instrument   |
| EXTVER    | 1        | Extension version number                | 1              | int   | csst_ms_sls_instrument   |
| BUNIT     | e-/s    | Brightness units                        | e-/s          | str  | csst_ms_sls_instrument   |
| NGOODPIX | 84794368 | Number of good pixels                   | -9999          | int  | csst_ms_sls_instrument   |
| GOODMAX   | 260.0    | Maxmum value of good pixels             | -9999          | float  | csst_ms_sls_instrument   |
| GOODMIN   | -0.001   | Minmum value of good pixels             | -9999          | float  | csst_ms_sls_instrument   |
| GOODMEAN  | 0.3      | Mean value of good pixels               | -9999          | float  | csst_ms_sls_instrument   |
| SNRMIN    | 187.4    | Minmum signal to noise of good pixels   | -9999          | float  | csst_ms_sls_instrument   |
| SNRMAX    | 1.2      | Maxmum signal to noise of good pixels   | -9999          | float  | csst_ms_sls_instrument   |
| SNRMEAN   | 3.38     | Average of the dark values subtracted   | -9999          | float  | csst_ms_sls_instrument   |

VER_INST 仪器改正版本号
STA_INST 仪器改正状态
STM_INST 仪器改正时间戳

#### Header of `csst_ms_sls_position`

位置定标信息新开一节
CD1_1等系数在修改后挪到这一节

| keyword  | value                 | comment                      | fallback_value | type   | module                |
|----------|:----------------------|------------------------------|----------------|--------|-----------------------|
| CTYPE1   | 'RA---TPV'            |                              | 'RA---TAN'     | str    | csst_ms_sls_position  |
| CTYPE2   | 'DEC--TPV'            |                              | 'DEC--TAN'     | str    | csst_ms_sls_position  |
| CUNIT1   | 'deg  '               |                              | 'deg'          | str    | csst_ms_sls_position  |
| CUNIT2   | 'deg  '               |                              | 'deg'          | str    | csst_ms_sls_position  |
| RADESYS  | 'ICRS '               |                              | '?'            | str    | csst_ms_sls_position  |
| PV1_0    | 0.003205383944913964  |                              | -9999          | f32    | csst_ms_sls_position  |
| PV1_1    | 0.8673020820536499    |                              | -9999          | f32    | csst_ms_sls_position  |
| PV1_2    | -0.2011989871377834   |                              | -9999          | f32    | csst_ms_sls_position  |
| PV1_3    | -0.2597214229472611   |                              | -9999          | f32    | csst_ms_sls_position  |
| PV1_4    | 0.4353828741811097    |                              | -9999          | f32    | csst_ms_sls_position  |
| PV1_5    | -0.5054216569802673   |                              | -9999          | f32    | csst_ms_sls_position  |
| PV1_6    | 0.1951474426617432    |                              | -9999          | f32    | csst_ms_sls_position  |
| PV2_0    | 0.00109803885992697   |                              | -9999          | f32    | csst_ms_sls_position  |
| PV2_1    | 0.9171065857705857    |                              | -9999          | f32    | csst_ms_sls_position  |
| PV2_2    | -0.04908256792722099  |                              | -9999          | f32    | csst_ms_sls_position  |
| PV2_3    | -0.09860562038448289  |                              | -9999          | f32    | csst_ms_sls_position  |
| PV2_4    | 0.07961855240788976   |                              | -9999          | f32    | csst_ms_sls_position  |
| PV2_5    | -0.2009224365497067   |                              | -9999          | f32    | csst_ms_sls_position  |
| PV2_6    | 0.1741954691884874    |                              | -9999          | f32    | csst_ms_sls_position  |
| *NS_POS  | 10                    | number of the stars          | --             | i8     | csst_ms_sls_position  |
| RA_OFF   | -0.0                  | mas in unit                  | -9999          | f32    | csst_ms_sls_position  |
| DEC_OFF  | 0.0                   | mas in unit                  | -9999          | f32    | csst_ms_sls_position  |
| RA_RMS   | 127.1                 | mas in unit                  | -9999          | f32    | csst_ms_sls_position  |
| DEC_RMS  | 60.4                  | mas in unit                  | -9999          | f32    | csst_ms_sls_position  |
| RA_CEN   | 193.299027            | center of detector in ra     | --             | f32    | csst_ms_sls_position  |
| DEC_CEN  | 26.08851              | center of detector in dec    | --             | f32    | csst_ms_sls_position  |
| *VER_POS | '1.0'                 | version of distortion        | '1.0'          | str    | csst_ms_sls_position  |
| *STM_POS | '2023-02-16 12:15:16' | time of last modification    | --             | str    | csst_ms_sls_position  |
| *STA_POS | 0                     | 0 for done, 1 for failure    | 1              | i8     |  csst_ms_sls_position |


#### Header of `csst_ms_sls_qc1`
| keyword        | value    | comment                      | fallback_value | type  | module          |
|----------------|:---------|------------------------------|----------------|-------|-----------------|
| *STA_QC1 QC1_S | 0        | 0 for success, 1 for failure | 1              | i8    | csst_ms_sls_qc1 |
| VER_QC1        | '0.0.1'  | QC1 pipeline version         | '0.0.1'        | str   | csst_ms_sls_qc1 |
| QC1_FLAG       | 0        | quality flags                | -99            | i16   | csst_ms_sls_qc1 |
+ STM_QC1
+ 
### HDU2

#### Header of `csst_ms_sls_instrument`

| keyword  | value         | comment                    | fallback_value | type    | module                  |
|----------|---------------|----------------------------|----------------|---------|-------------------------|
| XTENSION | IMAGE         | Image extension            | IMAGE          | str     | csst_ms_sls_instrument  |
| BITPIX   | -32           | Bits per data value        | -32            | int      | csst_ms_sls_instrument  |                 
| NAXIS    | 2             | Number of array dimensions | 2              | int      | csst_ms_sls_instrument  |                 
| NAXIS1   | 9216          | Size of the axis           | 9216           | int      | csst_ms_sls_instrument  |                 
| NAXIS2   | 9232          | Size of the axis           | 9232           | int      | csst_ms_sls_instrument  |
| PCOUNT   | 0             | Number of parameters       | 0              | int      | csst_ms_sls_instrument  |                         
| GCOUNT   | 1             | Number of groups           | 1              | int      | csst_ms_sls_instrument  |                                       
| EXTNAME  | ERR           | Extension name             | ERR            | str     | csst_ms_sls_instrument  |
| EXTVER   | 1             | Extension version number   | 1              | int      | csst_ms_sls_instrument  |
| BUNIT   | e-/s   | Brightness units           | e-/s    | str     | csst_ms_sls_instrument  |

### HDU3

#### Header of `csst_ms_sls_instrument`

| keyword   | value       | comment                    | fallback_value | type   | module                 |
|-----------|-------------|----------------------------|----------------|--------|------------------------|
| XTENSION  | IMAGE       | Image extension            | IMAGE          | str    | csst_ms_sls_instrument |
| BITPIX    | 16          | Bits per data value        | 16             | int     | csst_ms_sls_instrument |                 
| NAXIS     | 2           | Number of array dimensions | 2              | int     | csst_ms_sls_instrument |                 
| NAXIS1    | 9216        | Size of the axis           | 9216           | int     | csst_ms_sls_instrument |                 
| NAXIS2    | 9232        | Size of the axis           | 9232           | int     | csst_ms_sls_instrument |
| PCOUNT    | 0           | Number of parameters       | 0              | int     | csst_ms_sls_instrument |                         
| GCOUNT    | 1           | Number of groups           | 1              | int     | csst_ms_sls_instrument |
| EXTNAME   | DQ          | Extension name             | DQ             | str    | csst_ms_sls_instrument |
| EXTVER    | 1           | Extension version number   | 1              | int     | csst_ms_sls_instrument |
| BUNIT    | unitless    | Brightness units           | unitless       | str    | csst_ms_sls_instrument |

