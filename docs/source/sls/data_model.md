# L1-MBI Data model

## File: \*\_img_L1_1.fits

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
| SIMPLE  | True  | Fits standard | True           | bool | csst_sims |

### HDU1

#### Header of `csst_ms_sls_instrument`

| keyword  | value                 | comment                                        | fallback_value | type | module                 |
| -------- | :-------------------- | ---------------------------------------------- | -------------- | ---- | ---------------------- |
| INST_V   | '0.0.1 '              | instrument correction pipeline version         |                | str  | csst_ms_sls_instrument |
| INST_TOL | '2022-12-30T10:18:53' | Time of last modification                      |                | str  | csst_ms_sls_instrument |
| DATASUM  | '1352015684'          | Integrity check of data records                |                | str  | csst_ms_sls_instrument |
| NGOODPIX | 84794368              | number of good pixels                          |                | f32  | csst_ms_sls_instrument |
| SDQFLAGS | 31743                 | serious data quality flags                     |                | i16  | csst_ms_sls_instrument |
| GOODMAX  | 260.0                 | maxmum value of good pixels                    |                | f32  | csst_ms_sls_instrument |
| GOODMIN  | -0.001                | minmum value of good pixels                    |                | f32  | csst_ms_sls_instrument |
| GOODMEAN | 0.3                   | mean value of good pixels                      |                | f32  | csst_ms_sls_instrument |
| SNRMIN   | 187.4                 | minmum signal to noise of good pixels          |                | f32  | csst_ms_sls_instrument |
| SNRMAX   | 1.2                   | maxmum signal to noise of good pixels          |                | f32  | csst_ms_sls_instrument |
| SNRMEAN  | 3.38                  | average of the dark values subtracted          |                | f32  | csst_ms_sls_instrument |
| BUNIT    | electrons/s           | brightness units                               |                | str  | csst_ms_sls_instrument |
| EXTNAEM  | SCI                   | extension name                                 |                | str  | csst_ms_sls_instrument |


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
| FIT_STAR   | 10                   |                              | 0              | i8   | csst_ms_sls_position |
| RA_OFF     | -0.0                 | mas in unit                  | -99            | f32  | csst_ms_sls_position |
| DEC_OFF    | 0.0                  | mas in unit                  | -99            | f32  | csst_ms_sls_position |
| RA_STD     | 127.1                | mas in unit                  | -99            | f32  | csst_ms_sls_position |
| DEC_STD    | 60.4                 | mas in unit                  | -99            | f32  | csst_ms_sls_position |
| FIT_S　　　 | 0                    | 0 for success, 1 for failure | 1              | i8   | csst_ms_sls_position |

#### Header of `csst_ms_sls_qc1`
| keyword    | value                | comment                      | fallback_value | type | module               |
| ---------- | :------------------- | ---------------------------- | -------------- | ---- | -------------------- |
| QC1_S 　　　| 0                    | 0 for success, 1 for failure | 1              | i8   | csst_ms_sls_qc1      |


