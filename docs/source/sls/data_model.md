# L1-MBI Data model

## File: \*\_*_L1_1.fits

### File contents

| HDU  | data                    | note       |
| ---- | ----------------------- | ---------- |
| HDU0 | None                    | PrimaryHDU |
| HDU1 | reduced SCI (9k x 9k)   | ImageHDU   |
| HDU2 | reduced ERR (9k x 9k)   | ImageHDU   |
| HDU3 | reduced DQ (9k x 9k)    | ImageHDU   |

### HDU0

| keyword | value | comment       | fallback_value | type | module    |
| ------- | :---- | ------------- | -------------- | ---- | --------- |
| SIMPLE  | True  | Fits standard |  True          | bool | csst_ms_sls_instrument |
| BITPIX   | 8                     | array data value                            | 8              | i8   | csst_ms_sls_instrument|            
| NAXIS    | 0                     | Number of axes                              |  0             | i8   |csst_ms_sls_instrument|             
| EXTEND   | T                     | file may contain standard extensions        |   T           | bool | csst_ms_sls_instrument|             
| NEXTEND  | 3                     | Number of file extensions                   |   3            | i8   | csst_ms_sls_instrument |
| CRDS_VER | '0.0.1 '              | Version of CRDS file selection software used|   '0.0.1 '     | str  | csst_ms_sls_instrument |
| R_GAIN   | '*.gain.fits'         | Gain reference file name                    |   'N/A'        | str  | csst_ms_sls_instrument |
| R_READN  | '*.rn.fits'           | Read noise reference file name              |      'N/A'     | str  | csst_ms_sls_instrument |
| R_SATURA | '*.sat.fits'          | Saturation reference file name              |      'N/A'     | str  | csst_ms_sls_instrument |
| R_MASK   | '*.msk.fits'          | Mask reference file name                    |       'N/A'    | str  | csst_ms_sls_instrument |
| R_BIAS   | '*bias.fits'          | SuperBias reference file name               |      'N/A'     | str  | csst_ms_sls_instrument |
| R_DARK   | '*dark.fits'          | Dark reference file name                    |       'N/A'    | str  | csst_ms_sls_instrument |
| R_DFLAT  | '*flat.fits'          | Detector Flat reference file name           |         'N/A'  | str  | csst_ms_sls_instrument |
| R_SFLAT  | '*flat.fits'          | Spectrograph Flat reference file name       |        'N/A'   | str  | csst_ms_sls_instrument |
| S_DQINI  | T                  | Data Quality Initialization                 |    F            | bool | csst_ms_sls_instrument |
| S_SATURA | T                  | Saturation Checking                         |    F           | bool | csst_ms_sls_instrument |
| S_ERRINI | T                  | Error Initialization                        |     F          | bool | csst_ms_sls_instrument |
| S_BIAS   | T                  | Bias correction                             |    F            | bool | csst_ms_sls_instrument |
| S_DARK   | T                  | Dark correction                             |     F           | bool | csst_ms_sls_instrument |
| S_FLAT   | T                  | Flat field correction                       |       F         | bool | csst_ms_sls_instrument |
| DCP_VER  | '0.0.1 '              | detector-level calibration pipeline version |   '0.0.1 '    | str  | csst_ms_sls_instrument |
| DCP_TIME | '2022-12-30T10:18:53' | pipeline processing time                    |    '2022-12-30T10:18:53'  | str  | csst_ms_sls_instrument |
| HISTORY  |'**step complete.'     | record processing message                   |       'null'       | str  | csst_ms_sls_instrument |

### HDU1

#### Header of `csst_ms_sls_instrument`

| keyword  | value                 | comment                                     | fallback_value | type | module                 |
| -------- | :-------------------- | ------------------------------------------- | -------------- | ---- | ---------------------- |
| EXTNAEM  | SCI                   | extension name                              |   SCI          | str  | csst_ms_sls_instrument |
| EXTVER   | 1                     | extension version number                    |   1            | i8   | csst_ms_sls_instrument |
| BUNIT    | electrons/s           | brightness units                            |   electrons/s  | str  | csst_ms_sls_instrument |
| NGOODPIX | 84794368              | number of good pixels                       |    0            | f32  | csst_ms_sls_instrument |
| SDQFLAGS | 31743                 | serious data quality flags                  |    0           | i16  | csst_ms_sls_instrument |
| GOODMAX  | 260.0                 | maxmum value of good pixels                 |    0            | f32  | csst_ms_sls_instrument |
| GOODMIN  | -0.001                | minmum value of good pixels                 |    0            | f32  | csst_ms_sls_instrument |
| GOODMEAN | 0.3                   | mean value of good pixels                   |    0            | f32  | csst_ms_sls_instrument |
| SNRMIN   | 187.4                 | minmum signal to noise of good pixels       |    0            | f32  | csst_ms_sls_instrument |
| SNRMAX   | 1.2                   | maxmum signal to noise of good pixels       |    0            | f32  | csst_ms_sls_instrument |
| SNRMEAN  | 3.38                  | average of the dark values subtracted       |    0            | f32  | csst_ms_sls_instrument |



#### Header of `csst_ms_sls_position`

| keyword    | value                | comment                      | fallback_value | type | module               |
| ---------- | :------------------- | ---------------------------- | -------------- | ---- | -------------------- |
| CTYPE1     | 'RA---TPV'           |                              | 'RA---TPV'     | str  | csst_ms_sls_position |
| CTYPE2     | 'DEC--TPV'           |                              | 'DEC--TPV'     | str  | csst_ms_sls_position |
| CUNIT1     | 'deg  '              |                              | 'deg'          | str  | csst_ms_sls_position |
| CUNIT2     | 'deg  '              |                              | 'deg'          | str  | csst_ms_sls_position |
| RADESYS    | 'ICRS '              |                              | 'ICRS'         | str  | csst_ms_sls_position |
| PV1_0      | 0.003205383944913964 |                              | 0              | f32  | csst_ms_sls_position |
| PV1_1      | 0.8673020820536499   |                              | 0              | f32  | csst_ms_sls_position |
| PV1_2      | -0.2011989871377834  |                              | 0              | f32  | csst_ms_sls_position |
| PV1_3      | -0.2597214229472611  |                              | 0              | f32  | csst_ms_sls_position |
| PV1_4      | 0.4353828741811097   |                              | 0              | f32  | csst_ms_sls_position |
| PV1_5      | -0.5054216569802673  |                              | 0              | f32  | csst_ms_sls_position |
| PV1_6      | 0.1951474426617432   |                              | 0              | f32  | csst_ms_sls_position |
| PV2_0      | 0.00109803885992697  |                              | 0              | f32  | csst_ms_sls_position |
| PV2_1      | 0.9171065857705857   |                              | 0              | f32  | csst_ms_sls_position |
| PV2_2      | -0.04908256792722099 |                              | 0              | f32  | csst_ms_sls_position |
| PV2_3      | -0.09860562038448289 |                              | 0              | f32  | csst_ms_sls_position |
| PV2_4      | 0.07961855240788976  |                              | 0              | f32  | csst_ms_sls_position |
| PV2_5      | -0.2009224365497067  |                              | 0              | f32  | csst_ms_sls_position |
| PV2_6      | 0.1741954691884874   |                              | 0              | f32  | csst_ms_sls_position |
| STAR_FIT   | 10                   | number of the stars          | 0              | i8   | csst_ms_sls_position |
| RA_OFF     | -0.0                 | mas in unit                  | -99            | f32  | csst_ms_sls_position |
| DEC_OFF    | 0.0                  | mas in unit                  | -99            | f32  | csst_ms_sls_position |
| RA_RMS     | 127.1                | mas in unit                  | -99            | f32  | csst_ms_sls_position |
| DEC_RMS    | 60.4                 | mas in unit                  | -99            | f32  | csst_ms_sls_position |
| RA_CEN     | 193.299027           | center of detector in ra     | 0              | f32  | csst_ms_sls_position |
| DEC_CEN    | 26.08851             | center of detector in dec    | 0              | f32  | csst_ms_sls_position |
| VER_DIST   | '1.0'                | version of distortion        | '1.0'          | str  | csst_ms_sls_position |
| TOL_DIST   | '2023-02-16 12:15:16'| time of last modification    |                | str  | csst_ms_sls_position |
| STA_DIST   | 0                    | 0 for done, 1 for failure    | 1              | i8   | csst_ms_sls_position |


#### Header of `csst_ms_sls_qc1`
| keyword    | value                | comment                      | fallback_value | type | module               |
| ---------- | :------------------- | ---------------------------- | -------------- | ---- | -------------------- |
| QC1_S 　　　| 0                    | 0 for success, 1 for failure | 1              | i8   | csst_ms_sls_qc1      |
| VER_QC1    | '0.0.1'              | QC1 pipeline version         | '0.0.1'        | str  | csst_ms_sls_qc1      |
| QC1_FLAG   | 0                    | quality flags                | -99            | i16  | csst_ms_sls_qc1      |

### HDU2

#### Header of `csst_ms_sls_instrument`

| keyword  | value       | comment                     | fallback_value | type   | module                 |
| -------- | ----------- | --------------------------- | -------------- | -----  | ---------------------- |
| XTENSION | IMAGE       | Image extension             |      IAMGE          | str    | csst_ms_sls_instrument |
| BITPIX   | -32         | bits per data value         |         -32       | i8     | csst_ms_sls_instrument |                 
| NAXIS    | 2           | Number of array dimensions  |           2     | i8     | csst_ms_sls_instrument |                 
| NAXIS1   | 9216        | Size of the axis            |           9216     | i8     | csst_ms_sls_instrument |                 
| NAXIS2   | 9232        | Size of the axis            |           9232     | i8     | csst_ms_sls_instrument |
| PCOUNT   | 0           | number of parameters        |            0    | i8     | csst_ms_sls_instrument |                         
| GCOUNT   | 1           | number of groups            |          1  | i8     |csst_ms_sls_instrument|                                       
| EXTNAME  | ERR         | extension name              |          ERR      | str    | csst_ms_sls_instrument |
| EXTVER   | 1           | extension version number    |           1     | i8     | csst_ms_sls_instrument |
| BUNIT    | electrons/s | brightness units            |      electrons/s    | str    | csst_ms_sls_instrument |

### HDU3

#### Header of `csst_ms_sls_instrument`

| keyword  | value       | comment                     | fallback_value | type | module                 |
| -------- | ----------- | --------------------------- | -------------- | ---- | ---------------------- |
| XTENSION | IMAGE       | Image extension             |      IAMGE          | str  | csst_ms_sls_instrument |
| BITPIX   | 16          | bits per data value         |      16          | i8   | csst_ms_sls_instrument |                 
| NAXIS    | 2           | Number of array dimensions  |        2        | i8   | csst_ms_sls_instrument |                 
| NAXIS1   | 9216        | Size of the axis            |        9216        | i8   | csst_ms_sls_instrument |                 
| NAXIS2   | 9232        | Size of the axis            |        9232        | i8   | csst_ms_sls_instrument |
| PCOUNT   | 0           | number of parameters        |          0      | i8   | csst_ms_sls_instrument |                         
| GCOUNT   | 1           | number of groups            |        1      | i8   |csst_ms_sls_instrument|                                       
| EXTNAME  | DQ          | extension name              |        DQ      | str  | csst_ms_sls_instrument |
| EXTVER   | 1           | extension version number    |         1       | i8   | csst_ms_sls_instrument |
| BUNIT    | unitless    | brightness units            |         unitless     | str  | csst_ms_sls_instrument |

