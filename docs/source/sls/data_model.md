# SLS L1 Data Model

- **General Description** 
  - SLS L1 file contains image data.
- **Naming convention**
  - **Format**: `CSST_{facility}_{project}_{data_type}_{t_start}[14]_{t_end}[14]_{obs_id}[9]_{detector}[2]_L{level}[1]_{version}.fits`
  - **Example**: CSST_MSC_MS_SCI_20270626203558_20270626203828_100000066_01_L0_1.fits
  - **Tips**: Click [here](https://csst-proto.readthedocs.io/en/latest/ch07_simulation.html#naming-conventions) for regular expression.
- **Approximate Size**: 700MB
- **File Type**: FITS
- **Written by**:
- **Required by**:
- **Sections**:

| HDU   | data                    | note        |
|-------|-------------------------|-------------|
| HDU0  | None                    | PrimaryHDU  |
| HDU1  | reduced SCI (9k x 9k)   | ImageHDU    |
| HDU2  | reduced ERR (9k x 9k)   | ImageHDU    |
| HDU3  | reduced DQ (9k x 9k)    | ImageHDU    |
 

### *HDU0 --> HDU1

HDU0 修改 `NEXTEND=3`
模块之间用COMMENT隔开，例如
```
COMMENT ==================================================================      
COMMENT QC0 CHECK                                                               
COMMENT ==================================================================  
```
精简每个关键字的comment
`-`表示不可能失败，不会使用fill value

### HDU1

#### Header of `csst_ms_sls_instrument`

| keyword  | value                 | comment                                      | fill value | type   | last modified |
|----------|:----------------------|----------------------------------------------|------------|--------|---------------|
| EXTNAME  | 'SCI'                 | Extension name                               | 'SCI'      | str    | C7            |
| EXTVER   | 1                     | Extension version number                     | 1          | int    | C7            |
| BUNIT    | 'e-/s'                | Physical unit                                | 'ADU'      | str    | C7            |
| VER_INST | '0.0.1 '              | Instrument calibration pipeline version      | -          | str    | C7            |
| STM_INST | '2022-12-30T10:18:53' | Instrument pipeline processing time          | -          | str    | C7            |
| STA_INST | 0                     | Instrument calibration status                | 1          | int    | C7            |
| VER_CRDS | '0.0.1 '              | Version of CRDS file selection software used | -          | str    | C7            |
| R_GAIN   | '*.gain.fits'         | Gain reference file name                     | 'N/A'      | str    | C7            |
| R_MASK   | '*.msk.fits'          | Mask reference file name                     | 'N/A'      | str    | C7            |
| R_BIAS   | '*bias.fits'          | SuperBias reference file name                | 'N/A'      | str    | C7            |
| R_DARK   | '*dark.fits'          | Dark reference file name                     | 'N/A'      | str    | C7            |
| R_DFLAT  | '*flat.fits'          | Detector flat reference file name            | 'N/A'      | str    | C7            |
| STA_DQI  | 0                     | Data quality initialization status           | 1          | int    | C7            |
| STA_SATC | 0                     | Saturation checking status                   | 1          | int    | C7            |
| STA_ERRI | 0                     | Error initialization status                  | 1          | int    | C7            |
| STA_BIAS | 0                     | Bias correction status                       | 1          | int    | C7            |
| STA_DARK | 0                     | Dark correction status                       | 1          | int    | C7            |
| STA_FLAT | 0                     | Flat field correction status                 | 1          | int    | C7            |
| STA_CR   | 0                     | Cosmic ray rejection status                  | 1          | int    | C7            |
| NGOODPIX | 84794368              | Number of good pixels                        | -9999      | float  | C7            |
| GOODMIN  | -0.001                | Minmum value of good pixels                  | -9999      | float  | C7            |
| GOODMAX  | 260.0                 | Maxmum value of good pixels                  | -9999      | float  | C7            |
| GOODMEAN | 0.3                   | Mean value of good pixels                    | -9999      | float  | C7            |
| SNRMIN   | 187.4                 | Minmum signal to noise of good pixels        | -9999      | float  | C7            |
| SNRMAX   | 1.2                   | Maxmum signal to noise of good pixels        | -9999      | float  | C7            |
| SNRMEAN  | 3.38                  | Mean value of signal to noise of good pixels | -9999      | float  | C7            |
| MEANDARK | 0.3                   | Average of the dark values subtracted        | -9999      | float  | C7            |
| CRCOUNT  | 88988                 | Cosmic ray counts                            | -9999      | float  | C7            |

#### Header of `csst_ms_sls_position`

位置定标信息新开一节
CD1_1等系数在修改后挪到这一节


| keyword    | value                 | comment                                  | fill value | type   | module                 | last modified |
|------------|:----------------------|------------------------------------------|------------|--------|------------------------|---------------|
| VER_POS    | '1.0'                 | Version of distortion                    | -          | str    | csst_ms_sls_position   | C7            |
| STM_POS    | '2023-02-16 12:15:16' | Time of last modification                | -          | str    | csst_ms_sls_position   | C7            |
| STA_POS    | 0                     | 0 for done, 1 for failure                | 1          | i8     | csst_ms_sls_position   | C7            |
| CRPIX1     | 29758.0               | Coordinate reference pixel of x          | -          | f32    | csst_ms_sls_position   | C7            |
| CRPIX2     | -15644.0              | Coordinate reference pixel of y          | -          | f32    | csst_ms_sls_position   | C7            |
| CRVAL1     | 193.299027            | Coordinate reference value of x          | -          | f32    | csst_ms_sls_position   | C7            |
| CRVAL2     | 26.08851              | Coordinate reference value of y          | -          | f32    | csst_ms_sls_position   | C7            |
| CTYPE1     | 'RA---TPV'            | Type of ra                               | 'RA---TAN' | str    | csst_ms_sls_position   | C7            |
| CTYPE2     | 'DEC--TPV'            | Type of dec                              | 'DEC--TAN' | str    | csst_ms_sls_position   | C7            |
| CD1_1_L0   | -8.1745583617600E-06  | Partial of first axis coordinate of x    | -          | f32    | csst_ms_sls_position   | C7            |
| CD2_1_L0   | 1.88602083707394E-05  | Partial of first axis coordinate of y    | -          | f32    | csst_ms_sls_position   | C7            |
| CD1_2_L0   | -1.8860208370739E-05  | Partial of second axis coordinate of x   | -          | f32    | csst_ms_sls_position   | C7            |
| CD2_2_L0   | -8.1745583617600E-06  | Partial of second axis coordinate of y   | -          | f32    | csst_ms_sls_position   | C7            |
| CD1_1      | -8.1745583617600E-06  | Partial of first axis coordinate of x    | -          | f32    | csst_ms_sls_position   | C7            |
| CD2_1      | 1.88602083707394E-05  | Partial of first axis coordinate of y    | -          | f32    | csst_ms_sls_position   | C7            |
| CD1_2      | -1.8860208370739E-05  | Partial of second axis coordinate of x   | -          | f32    | csst_ms_sls_position   | C7            |
| CD2_2      | -8.1745583617600E-06  | Partial of second axis coordinate of y   | -          | f32    | csst_ms_sls_position   | C7            |
| CUNIT1     | 'deg  '               | Unit of ra                               | 'deg'      | str    | csst_ms_sls_position   | C7            |
| CUNIT2     | 'deg  '               | Unit of dec                              | 'deg'      | str    | csst_ms_sls_position   | C7            |
| RADESYS    | 'ICRS '               | International celestial reference system | -          | str    | csst_ms_sls_position   | C7            |
| PV1_0      | 0.003205383944913964  | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV1_1      | 0.8673020820536499    | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV1_2      | -0.2011989871377834   | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV1_3      | -0.2597214229472611   | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV1_4      | 0.4353828741811097    | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV1_5      | -0.5054216569802673   | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV1_6      | 0.1951474426617432    | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV2_0      | 0.00109803885992697   | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV2_1      | 0.9171065857705857    | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV2_2      | -0.04908256792722099  | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV2_3      | -0.09860562038448289  | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV2_4      | 0.07961855240788976   | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV2_5      | -0.2009224365497067   | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| PV2_6      | 0.1741954691884874    | PV coefficients                          | -9999      | f32    | csst_ms_sls_position   | C7            |
| NS_POS     | 10                    | Number of the stars                      | 0          | i8     | csst_ms_sls_position   | C7            |
| RA_OFF     | -0.0                  | Mas in unit                              | -9999      | f32    | csst_ms_sls_position   | C7            |
| DEC_OFF    | 0.0                   | Mas in unit                              | -9999      | f32    | csst_ms_sls_position   | C7            |
| RA_RMS     | 127.1                 | Mas in unit                              | -9999      | f32    | csst_ms_sls_position   | C7            |
| DEC_RMS    | 60.4                  | Mas in unit                              | -9999      | f32    | csst_ms_sls_position   | C7            |
| RA_CEN     | 193.299027            | Center of detector in ra                 | -9999      | f32    | csst_ms_sls_position   | C7            |
| DEC_CEN    | 26.08851              | Center of detector in dec                | -9999      | f32    | csst_ms_sls_position   | C7            |


#### Header of `csst_ms_sls_qc1`
| keyword        | value                     | comment                      | fill value | type  | last modified |
|----------------|:--------------------------|------------------------------|------------|-------|---------------|
| STA_QC1        | 0                         | 0 for success, 1 for failure | -1         | i8    | C7            |
| VER_QC1        | '0.0.1'                   | QC1 pipeline version         | '0.0.1'    | str   | C7            |
| FLG_QC1        | 0                         | Quality flags                | -9999      | i16   | C7            |
| STM_QC1        | '2023-02-16T12:15:16'     | QC1 pipeline processing time | -          | str   | C7            | 
 
### HDU2

#### Header of `csst_ms_sls_instrument`

| keyword  | value    | comment                    | fill value | type      | last modified |
|----------|----------|----------------------------|------------|-----------|---------------|
| XTENSION | 'IMAGE'  | Image extension            | -          | str       | C7            |
| BITPIX   | -32      | Bits per data value        | -          | int       | C7            |                 
| NAXIS    | 2        | Number of array dimensions | -          | int       | C7            |                 
| NAXIS1   | 9216     | Size of the axis           | -          | int       | C7            |                 
| NAXIS2   | 9232     | Size of the axis           | -          | int       | C7            |
| PCOUNT   | 0        | Number of parameters       | -          | int       | C7            |                         
| GCOUNT   | 1        | Number of groups           | -          | int       | C7            |                                       
| EXTNAME  | 'ERR'    | Extension name             | 'ERR'      | str       | C7            |
| EXTVER   | 1        | Extension version number   | 1          | int       | C7            |
| BUNIT    | 'e-/s'   | Physical unit              | 'ADU'      | str       | C7            |

### HDU3

#### Header of `csst_ms_sls_instrument`

| keyword  | value       | comment                    | fill value     | type     | last modified |
|----------|-------------|----------------------------|----------------|----------|---------------|
| XTENSION | 'IMAGE'     | Image extension            | -              | str      | C7            |
| BITPIX   | 16          | Bits per data value        | -              | int      | C7            |                 
| NAXIS    | 2           | Number of array dimensions | -              | int      | C7            |                 
| NAXIS1   | 9216        | Size of the axis           | -              | int      | C7            |                 
| NAXIS2   | 9232        | Size of the axis           | -              | int      | C7            |
| PCOUNT   | 0           | Number of parameters       | -              | int      | C7            |                         
| GCOUNT   | 1           | Number of groups           | -              | int      | C7            |
| EXTNAME  | 'DQ'        | Extension name             | 'DQ'           | str      | C7            |
| EXTVER   | 1           | Extension version number   | 1              | int      | C7            |
| BUNIT    | 'UNITLESS'  | Physical unit              | 'UNITLESS'     | str      | C7            |

