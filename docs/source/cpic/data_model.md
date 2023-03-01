# L1-CPI-C Data model

- `---`表示在模块算法失败的情况下按照实际情况填写，比如无论模块是否成功，时间戳都应该填写实际值

## File: *_VIS_SCI_*.*fits

### File contents

| HDU  | data                                            | note       |
|------|-------------------------------------------------|------------|
| HDU0 | None                                            | PrimaryHDU |
| HDU1 | [reduced image (1k x 1k), mask image (1k x 1k)] | ImageHDU   |
| HDU2 | [reduced image (1k x 1k), mask image (1k x 1k)] | ImageHDU   |
| ...  | ...                                             | ImageHDU   |
| HDUn | [reduced image (1k x 1k), mask image (1k x 1k)] | ImageHDU   |

### HDU0

| keyword | value | comment       | fill value    | type | module    |
|---------|:------|---------------|---------------|------|-----------|
| SIMPLE  | True  | Fits standard | True          | bool | csst_sims |     

### HDUn

| keyword   | value                 | comment                                         | fill value   | type | module                   |
|-----------|:----------------------|-------------------------------------------------|--------------|------|--------------------------|
|  VER_PIPE | '0.01'                | version of CPI-C pipeline                       | '0.01'       | str  | csst_cpic                |
|  VER_QC0  | '0.01'                | version of CPI-C QC0                            | '0.01'       | str  | csst_cpic                |
|  VER_QC1  | '0.01'                | version of CPI-C QC1                            | '0.01'       | str  | csst_cpic                |
|  STA_PIPE | 0                     | state of CPI-C pipeline                         | 1            | i8   | csst_cpic                |
|  STA_QC0  | 0                     | state of CPI-C QC0                              | 1            | i8   | csst_cpic                |
|  STA_QC1  | 0                     | state of CPI-C QC1                              | 1            | i8   | csst_cpic                |
|  STM_PIPE | '2022-12-30T10:18:53' | Time stamp of CPI-C pipeline processing         | ---          | str  | csst_cpic                |
|  NAME     | 'HR 8799'             | name of target                                  | ---          | str  | csst_cpic                |
|  I_MEAN   | 10.0                  | mean value of total noise of dark zone          | -9999        | f32  | csst_cpic                |        
|  I_STD    | 1833.333333333333     | std value of total noise of dark zone           | -9999        | f32  | csst_cpic                |
|  I_MARK   | 'S'                   | Status flag for image classify                  | 'S'          | str  | csst_cpic                |
|  CTE_NAM  | 'CTE.fits'            | name of CTE reference file                      | '-1'         | str  | csst_cpic                |
|  CTEV_VAL | 99.99                 | value of vertical CTE                           | -9999        | f32  | csst_cpic                |
|  CTEH_VAL | 99.99                 | value of horizontal CTE                         | -9999        | f32  | csst_cpic                |
|  BP_NAM   | 'mask.fits'           | name of mask reference file                     | '-1'         | f32  | csst_cpic                |
|  BP_NUM   | 10                    | number of bad pixel                             | -1           | i16  | csst_cpic                |
|  B_NAM    | 'bias.fits'           | name of bias reference file                     | -1           | str  | csst_cpic                |
|  B_MEAN   | 5.1                   | mean value of bias reference image              | -9999        | f32  | csst_cpic                |
|  B_STD    | 1.2                   | std value of bias reference image               | -9999        | f32  | csst_cpic                | 
|  SP_NUM   | 10                    | number of saturated pixels                      | -1           | i16  | csst_cpic                |
|  D_NAM    | 'dark.fits'           | name of dark reference file                     | '-1'         | str  | csst_cpic                |
|  D_MEAN   | 0.1                   | mean value of dark reference image              | -9999        | f32  | csst_cpic                |
|  D_STD    | 0.1                   | std value of dark reference image               | -9999        | f32  | csst_cpic                |
|  F_NAM    | 'flat.fits'           | name of flat reference file                     | -1           | str  | csst_cpic                |
|  F_MEAN   | 10.0                  | mean value of flat reference image              | -9999        | f32  | csst_cpic                |
|  F_STD    | 5.0                   | std value of flat reference image               | -9999        | f32  | csst_cpic                |
|  NL_NAM   | 'nonlin.fits'         | name of nonlinear correction reference file     | -1           | str  | csst_cpic                |
|  BG_NAM   | 'bg.fits'             | name of background reference file               | -1           | str  | csst_cpic                |
|  CR_MOD   | 'lacosmic'            | mode of CR clean. 'lacosmic' or 'deepCR'        | -1           | str  | csst_cpic                |
|  CR_NUM   | 10                    | number of cosmic ray                            | -1           | i16  | csst_cpic                | 



| keyword   | value                 | comment                                         | fill value   | type | module                   |
|-----------|:----------------------|-------------------------------------------------|--------------|------|--------------------------|
|  FLAG     | 0                     | normal pixels                                   | 0            | i8   | csst_cpic                |
|  FLAG     | 1                     | bad pixels                                      | 0            | i8   | csst_cpic                |
|  FLAG     | 2                     | hot pixels                                      | 0            | i8   | csst_cpic                |
|  FLAG     | 4                     | warm pixels                                     | 0            | i8   | csst_cpic                |
|  FLAG     | 8                     | saturated pixels                                | 0            | i8   | csst_cpic                |
|  FLAG     | 16                    | pixels contaminated by cosmic ray               | 0            | i8   | csst_cpic                |
|  FLAG     | 32                    | pixels contaminated by sputnik                  | 0            | i8   | csst_cpic                |