# L1-IFS Data model

## File: CSST_IFS_CUBE_{OBJ_id}_{VER_cube}_{LIN/LOG}_{STM_cube}.fits

### File contents

| HDU  | data                    | note       |
|------|-------------------------|------------|
| HDU0 | None                    | PrimaryHDU |
| HDU1 | FLUX                    | ImageHDU   |
| HDU2 | IVAR                    | ImageHDU   |
| HDU3 | MASK                    | ImageHDU   |
| HDU4 | EXP_NUM                 | ImageHDU   |
| HDU5 | LSF                     | ImageHDU   |
| HDU6 | WEIGHT_MARTIX           | ImageHDU   |
| HDU7 | rRSS_FILE_LIST          | BinTableHDU|

### HDU0

#### Header of `csst_ifs_cube`

| keyword   | value                 | comment                                           | fill value   | type | module                   |
|-----------|:----------------------|---------------------------------------------------|--------------|------|--------------------------|
| RSS_VER   | R6100                 | version of RSS code                               | RXXXX        |str   | csst_ifs_cube            |
| CUB_VER   | C6100                 | version of CUBE code                              | CXXXX        |str   | csst_ifs_cube            |
| COV_VER   | C6100                 | version of CUBE code                              | CXXXX        |str   | csst_ifs_cube            |
| LSF_VER   | C6100                 | version of CUBE code                              | CXXXX        |str   | csst_ifs_cube            |
| FLUXUNIT  | '1E-17 erg/s/cm2/A/arcsec2' | unit of flux                                | '1E-17 erg/s/cm2/A/arcsec2'|str   | csst_ifs_cube |
| FLUXSCALE | 1                     | Intensity unit scaling                            | 1            |I8    | csst_ifs_cube            |
| FLUXZERO  | 0                     | Intensity zeropoint                               | 0            |I8    | csst_ifs_cube            |
|TELESCOP	| CSST                  | Telescope used to acquire data		            | CSST         |str   | csst_ifs_cube            |
|INSTRUMENT	| IFS                   | Identifier for instrument used to acquire data    | IFS          |str   | csst_ifs_cube            |
|OBJID      | 174053.8-534326'      | ID of Object(in the form of HHMMSS.S+DDMMSS)      | hhmmss.sddmmss|str  | csst_ifs_cube            |
|NEXP       | 50                    | number of science exposures combined              | 0            |I8    | csst_ifs_cube            |
|EXPTIME    | 60000                 | Total exposure time                               | 0            |f32   | csst_ifs_cube            |
|MJDMIN     | 2459955.2275463       | Minimum OBS MJD across all exposures              | -9999        |f32   | csst_ifs_cube            |
|MJDMAX     | 2459955.39282407      | Maximum OBS MJD across all exposures              | -9999        |f32   | csst_ifs_cube            |
|MJDMED     | 2459955.34074074      | Median OBS MJD across all exposures               | -9999        |f32   | csst_ifs_cube            |
|WCSCAL_VER | A6101                 | Version of WCS calibration	                    | AXXX         |str   | csst_ifs_cube            |
|WCSCAL_P	|                       | file for WCS calibration 	                        |  "?"         |str   | csst_ifs_cube            |
|RADECSYS	| FK5                   | Frame of reference of coordinates                 | FK5          |str   | csst_ifs_cube            |
|EQUINOX    | 2000.0                |                                                   | 2000.0       |str   | csst_ifs_cube            |
|OBJRA	    | 265.22407917          | Object R.A. (J2000 deg.)                          | -9999        |f32   | csst_ifs_cube            |
|OBJDEC     | -53.72406389          | Object Dec. (J2000 deg.)                          | -9999        |f32   | csst_ifs_cube            |
|CENRA	    | 265.2240087483441     | Plate center R.A. (J2000 deg.)	R4	            | -9999        |f32   | csst_ifs_cube            |
|CENDEC	    | -53.72410555664603    | Plate center Dec. (J2000 deg.)	R4	            | -9999        |f32   | csst_ifs_cube            |
|CTYPE3	    | 'LIN'                 | The type of wavelength array                      | 'LIN'        |str   | csst_ifs_cube            |
|CRPIX3	    | 1.0                   | Starting pixel	                                | -9999        |f32   | csst_ifs_cube            |
|CRVAL3	    | 3500.0                | The central wavelength wv0 of first pixel 	    | -9999        |f32   | csst_ifs_cube            |
|CD3_3	    | 1.75                  | wavelength dispersion per pixel	                | -9999        |f32   | csst_ifs_cube            |
|CUNIT3	    | 'Angstrom'            | unit of wavelength                                | 'Angstrom'   |str   | csst_ifs_cube            |
|CRPIX1	    | 49.0                  | Reference pixel	                                | -9999        |f32   | csst_ifs_cube            |
|CRPIX2	    | 52.0                  | Reference pixel	                                | -9999        |f32   | csst_ifs_cube            |
|CRVAL1	    | 265.22407917          | RA of reference point	                            | -9999        |f32   | csst_ifs_cube            |
|CRVAL2     | -53.72406389	        | Dec of reference point	                        | -9999        |f32   | csst_ifs_cube            |
|CD1_1	    | -2.7777777777777E-05  | Coordinate transformation matrix element	        | -9999        |f32   | csst_ifs_cube            |
|CD1_2	    | 0.0                   | Coordinate transformation matrix element	        | -9999        |f32   | csst_ifs_cube            |
|CD2_1	    | 0.0                   | Coordinate transformation matrix element	        | -9999        |f32   | csst_ifs_cube            |
|CD2_2	    | 2.7777777777778E-05   | Coordinate transformation matrix element	        | -9999        |f32   | csst_ifs_cube            |
|CTYPE1     | 'RA---TAN'	        | Declination, gnomonic projection	                | 'RA---TAN'   |str   | csst_ifs_cube            |
|CTYPE2     | 'DEC--TAN'	        | Declination, gnomonic projection	                | 'DEC--TAN'   |str   | csst_ifs_cube            |
|CUNIT1	    | 'deg'                 | Units of coordinate increment and value	        | 'deg'        |str   | csst_ifs_cube            |
|CUNIT2	    | 'deg'                 | Units of coordinate increment and value	        | 'deg'        |str   | csst_ifs_cube            |
|EBVGAL     | 0	                    | Galactic reddening E(B-V)	                        | -9999        |f32   | csst_ifs_cube            |
|CHECKSUM   | 0                     |checksum                                           | 1            |I8    | csst_ifs_cube            |
