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

| keyword            | value                  | comment                                       | fallback_value        | type   | last modified                  |
|--------------------|:-----------------------|-----------------------------------------------|-----------------------|--------|-------------------------|
| VER_CRDS           | '0.0.1 '               | Version of CRDS file selection software used  | -                     | str    | C7  |
| R_GAIN             | '*.gain.fits'          | Gain reference file name                      | 'N/A'                 | str    | C7  |
| R_READN            | '*.rn.fits'            | Read noise reference file name                | 'N/A'                 | str    | C7  |
| R_SATURA           | '*.sat.fits'           | Saturation reference file name                | 'N/A'                 | str    | C7  |
| R_MASK             | '*.msk.fits'           | Mask reference file name                      | 'N/A'                 | str    | C7  |
| R_BIAS             | '*bias.fits'           | SuperBias reference file name                 | 'N/A'                 | str    | C7  |
| R_DARK             | '*dark.fits'           | Dark reference file name                      | 'N/A'                 | str    | C7  |
| R_DFLAT            | '*flat.fits'           | Detector Flat reference file name             | 'N/A'                 | str    | C7  |
| STA_DQINI            | 0                    | Data Quality Initialization status             | 1                     | int  | C7  |
| STA_SATURA           | 0                      | Saturation Checking status                 | 1                     | int   | C7  |
| STA_ERRINI           | 0                      | Error Initialization status                 |1                     | int   | C7  |
| STA_BIAS             | 0                      | Bias correction status                      | 1                     | int   | C7  |
| STA_DARK             | 0                     | Dark correction status                       | 1                     | int   | C7  |
| STA_FLAT             | 0                      | Flat field correction status                 | 1                     | int   | C7  |
| VER_INST           | '0.0.1 '               | Instrument calibration pipeline version   | -                     | str    | C7 |
| STA_INST        | 0  | Instrument calibration status | 1 | int | C7 |
| STM_INST | '2022-12-30T10:18:53'  | Instrument pipeline processing time             | -  | str    | C7  |
| HISTORY            | '**step complete.'     | Record processing message                     | -              | str    | C7  |

### HDU1

#### Header of `csst_ms_sls_instrument`


| keyword   | value    | comment                                 | fallback_value | type | last modified                   |
|-----------|:---------|-----------------------------------------|----------------|------|--------------------------|
| EXTNAME   | 'SCI'      | Extension name                          | 'SCI'            | str  | C7   |
| EXTVER    | 1        | Extension version number                | 1              | int   | C7   |
| BUNIT     | 'e-/s'    | Brightness units                        | 'e-/s'          | str  | C7   |
| NGOODPIX | 84794368 | Number of good pixels                   | -9999          | float  | C7   |
| GOODMAX   | 260.0    | Maxmum value of good pixels             | -9999          | float  | C7   |
| GOODMIN   | -0.001   | Minmum value of good pixels             | -9999          | float  | C7   |
| GOODMEAN  | 0.3      | Mean value of good pixels               | -9999          | float  | C7   |
| SNRMIN    | 187.4    | Minmum signal to noise of good pixels   | -9999          | float  | C7   |
| SNRMAX    | 1.2      | Maxmum signal to noise of good pixels   | -9999          | float  | C7  |
| SNRMEAN   | 3.38     | Average of the dark values subtracted   | -9999          | float  | C7   |
| CRCOUNT  | 88988 | Cosmic ray counts | -9999 | float | C7 |
VER_INST 仪器改正版本号 
STA_INST 仪器改正状态
STM_INST 仪器改正时间戳

#### Header of `csst_ms_sls_position`

位置定标信息新开一节
CD1_1等系数在修改后挪到这一节

| keyword  | value                 | comment                      | fallback_value | type   | module                | last modified |
|----------|:----------------------|------------------------------|----------------|--------|-----------------------|------|
| CTYPE1   | 'RA---TPV'            | type of ra                   | 'RA---TAN'     | str    | csst_ms_sls_position  | C7   |
| CTYPE2   | 'DEC--TPV'            | type of dec                  | 'DEC--TAN'     | str    | csst_ms_sls_position  | C7   |
| CUNIT1   | 'deg  '               | unit of ra                   | 'deg'          | str    | csst_ms_sls_position  | C7   |
| CUNIT2   | 'deg  '               | unit of dec                  | 'deg'          | str    | csst_ms_sls_position  | C7   |
| RADESYS  | 'ICRS '               | international celestial reference system | -  | str    | csst_ms_sls_position  | C7   |
| PV1_0    | 0.003205383944913964  | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV1_1    | 0.8673020820536499    | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV1_2    | -0.2011989871377834   | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV1_3    | -0.2597214229472611   | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV1_4    | 0.4353828741811097    | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV1_5    | -0.5054216569802673   | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV1_6    | 0.1951474426617432    | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV2_0    | 0.00109803885992697   | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV2_1    | 0.9171065857705857    | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV2_2    | -0.04908256792722099  | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV2_3    | -0.09860562038448289  | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV2_4    | 0.07961855240788976   | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV2_5    | -0.2009224365497067   | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| PV2_6    | 0.1741954691884874    | pv coefficients              | -9999          | f32    | csst_ms_sls_position  | C7   |
| NS_POS   | 10                    | number of the stars          | --             | i8     | csst_ms_sls_position  | C7   |
| RA_OFF   | -0.0                  | mas in unit                  | -9999          | f32    | csst_ms_sls_position  | C7   |
| DEC_OFF  | 0.0                   | mas in unit                  | -9999          | f32    | csst_ms_sls_position  | C7   |
| RA_RMS   | 127.1                 | mas in unit                  | -9999          | f32    | csst_ms_sls_position  | C7   |
| DEC_RMS  | 60.4                  | mas in unit                  | -9999          | f32    | csst_ms_sls_position  | C7   |
| RA_CEN   | 193.299027            | center of detector in ra     | --             | f32    | csst_ms_sls_position  | C7   |
| DEC_CEN  | 26.08851              | center of detector in dec    | --             | f32    | csst_ms_sls_position  | C7   |
| VER_POS  | '1.0'                 | version of distortion        | '1.0'          | str    | csst_ms_sls_position  | C7   |
| STM_POS  | '2023-02-16 12:15:16' | time of last modification    | --             | str    | csst_ms_sls_position  | C7   |
| STA_POS  | 0                     | 0 for done, 1 for failure    | 1              | i8     |  csst_ms_sls_position | C7   |


#### Header of `csst_ms_sls_qc1`
| keyword        | value                    | comment                      | fallback_value | type  | last modified |
|----------------|:-------------------------|------------------------------|----------------|-------|---------------|
| STA_QC1        | 0                        | 0 for success, 1 for failure | -1             | i8    | C7            |
| VER_QC1        | '0.0.1'                  | QC1 pipeline version         | '0.0.1'        | str   | C7            |
| QC1_FLAG       | 0                        | Quality flags                | -9999          | i16   | C7            |
| STM_QC1        | '2023-02-16T12:15:16'    | QC1 pipeline processing time | -              | str   | C7            | 
 
### HDU2

#### Header of `csst_ms_sls_instrument`

| keyword  | value         | comment                    | fallback_value | type    | last modified                  |
|----------|---------------|----------------------------|----------------|---------|-------------------------|
| XTENSION | 'IMAGE'         | Image extension            | 'IMAGE'          | str     | C7  |
| BITPIX   | -32           | Bits per data value        | -32            | int      | C7  |                 
| NAXIS    | 2             | Number of array dimensions | 2              | int      | C7  |                 
| NAXIS1   | 9216          | Size of the axis           | 9216           | int      | C7  |                 
| NAXIS2   | 9232          | Size of the axis           | 9232           | int      | C7  |
| PCOUNT   | 0             | Number of parameters       | 0              | int      | C7  |                         
| GCOUNT   | 1             | Number of groups           | 1              | int      | C7 |                                       
| EXTNAME  | 'ERR'           | Extension name             | 'ERR'            | str     | C7  |
| EXTVER   | 1             | Extension version number   | 1              | int      | C7  |
| BUNIT   | 'e-/s'   | Brightness units           | 'e-/s'    | str     | C7  |

### HDU3

#### Header of `csst_ms_sls_instrument`

| keyword   | value       | comment                    | fallback_value | type   | last modified                |
|-----------|-------------|----------------------------|----------------|--------|------------------------|
| XTENSION  | 'IMAGE'       | Image extension            | 'IMAGE'          | str    | C7 |
| BITPIX    | 16          | Bits per data value        | 16             | int     | C7 |                 
| NAXIS     | 2           | Number of array dimensions | 2              | int     | C7 |                 
| NAXIS1    | 9216        | Size of the axis           | 9216           | int     | C7 |                 
| NAXIS2    | 9232        | Size of the axis           | 9232           | int     | C7 |
| PCOUNT    | 0           | Number of parameters       | 0              | int     | C7 |                         
| GCOUNT    | 1           | Number of groups           | 1              | int     | C7 |
| EXTNAME   | 'DQ'          | Extension name             | 'DQ'             | str    | C7 |
| EXTVER    | 1           | Extension version number   | 1              | int     | C7 |
| BUNIT    | 'unitless'    | Brightness units           | 'unitless'       | str    | C7 |

