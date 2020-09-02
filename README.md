
# arduino-psa-telematic-diag
Arduino sketch to send diagnostic frames to telematic units

## How to use
The serial console is used to send raw diagnostic frames, start it using 115200 baud rate

## Commands

| Command | Description |
|--|--|
| 190209 | List of current faults |
| 14FFFFFF | Clear faults |
| 37 | Flash autocontrol (Unit must be unlocked first) |
| 1001 | End of communication |
| 1002 | Open Download session |
| 1003 | Open Diagnostic session |
| 1103 | Reboot |
| 2701 | Unlocking service for download (Diagnostic session must be enabled first) - SEED |
| 2703 | Unlocking service for configuration (Diagnostic session must be enabled first) - SEED |
| 2702XXXXXXXX  | Unlocking response for download - XXXXXXXX = KEY - Must be given within 5 seconds after seed generation |
| 2704XXXXXXXX  | Unlocking response for configuration - XXXXXXXX = KEY - Must be given within 5 seconds after seed generation |
| 22XXXX | Read Zone XXXX (2 bytes) |
| 2EXXXXYYYYYYYYYYYY | Write Zone XXXX with data YYYYYYYYYYYY (Unit must be unlocked first) |
| 3101FF0081F05A | Empty flash memory (Unit must be unlocked first) |
| 3103FF00 | Empty flash memory (Unit must be unlocked first) |
| 3481110000 | Prepare flash writing (Unit must be unlocked first) |
| 3101FF04 | Empty ZI Zone (Unit must be unlocked first) |
| 3103FF04 | Empty ZI Zone (Unit must be unlocked first) |
| 3483110000 | Prepare ZI zone writing (Unit must be unlocked first) |

## Test Commands
| Command | Description |
|--|--|
| 22D4XX | Measures |
| 22D405 | Visible satellites |
| 3101DF07 | NAC/RCC: Tactile Test Screen |
| 2FD6000300 | NAC/RCC: Black screen |
| 2FD60000 | NAC/RCC: Restore the screen |
| 2FD66000 | NAC/RCC: Stop Camera display control |
| 2FD66003 | NAC/RCC: Camera display control |
| 2FD6700330 | NAC/RCC: 180° Camera display control - Standard view |
| 2FD6700340 | NAC/RCC: 180° Camera display control - Zoom view |
| 2FD6700350 | NAC/RCC: 180° Camera display control - Lateral view |
| 2FD62000 | NAC/RCC: Stop Sound Test |
| 082FD620030108 | NAC/RCC: Sound test Front Right |
| 082FD62003010A | NAC/RCC: Sound test Front Right |
| 082FD620030208 | NAC/RCC: Sound test Front Left |
| 082FD62003020A | NAC/RCC: Sound test Front Left |
| 082FD620030308 | NAC/RCC: Sound test Back Right |
| 082FD62003030A | NAC/RCC: Sound test Back Right |
| 082FD620030308 | NAC/RCC: Sound test Back Left |
| 082FD62003030A | NAC/RCC: Sound test Back Left |

## Answers

| Answer | Description |
|--|--|
| 54 | Faults cleared |
| 7101FF0001 | Flash erased successfully |
| 7103FF0002 | Flash erased successfully |
| 7101FF0401 | ZI erased successfully |
| 7103FF0402 | ZI erased successfully |
| 77 | Flash autocontrol OK |
| 5001XXXXXXXX | Communication closed |
| 5002XXXXXXXX | Download session opened |
| 5003XXXXXXXX | Diagnostic session opened |
| 5103 | Reboot OK |
| 62XXXXYYYYYYYYYYYY  | Successfull read of Zone XXXX - YYYYYYYYYYYY = DATA |
| 6701XXXXXXXX | Seed generated for download - XXXXXXXX = SEED |
| 6703XXXXXXXX | Seed generated for configuration - XXXXXXXX = SEED |
| 6702 | Unlocked successfully for download - Unit will be locked again if no command is issued within 5 seconds |
| 6704 | Unlocked successfully for configuration - Unit will be locked again if no command is issued within 5 seconds |
| 6EXXXX | Successfull Configuration Write of Zone XXXX |
| 741000 | Download Writing ready |
| 76XX02 | Download frame XX injected with success |
| 76XX0A | Invalid checksum on download frame XX |
| 7F3478 | Download Writing in progress |
| 7F3778 | Flash autocontrol in progress |
| 7F2724 | Anti-Bruteforce active |
| 7F2713 | Invalid SEED Answer (KEY) |
| 7F2E78 | Configuration Write in progress |
| 7F2E13 | Failed Configuration Write - Invalid Zone data |
| 7F2E7E | Failed Configuration Write - Unit is locked |
| 7F2E31 | Failed Configuration Write - Not allowed operation |
| 7F2EXX | Failed Configuration Write |
| 7F2E31 | Failed Configuration Read - Not allowed operation |
| 7F22XX | Failed Configuration Read |
| 7FXXYY | Error - XX = Service / YY = Error Number |

## Zones

| Zone ID | Description |
|--|--|
| F0FE | ZI Zone (Last 6 characters: current calibration) |
| F080 | ZA Zone |
| F190 | VIN |
| F18C | NAC/RCC Serial number |
| 2100 | NAC/RCC: Telecoding_Fct_AAS |
| 2101 | NAC/RCC: Telecoding_Fct_AFIL |
| 1234 | NAC/RCC: HU_CODING_ADDONS |
| 2103 | NAC/RCC: Telecoding_Fct_ARTIV |
| 2104 | NAC/RCC: Telecoding_Fct_AUDIO |
| 2106 | NAC/RCC: Telecoding_Fct_AVR |
| 2107 | NAC/RCC: Telecoding_Fct_BT |
| 2108 | NAC/RCC: Telecoding_Fct_BTEL |
| 2109 | NAC/RCC: Telecoding_Fct_CAFR |
| 210A | NAC/RCC: Telecoding_Fct_CHANGER_CD |
| 210B | NAC/RCC: Telecoding_Fct_CHECK |
| 210C | NAC/RCC: Telecoding_Fct_CITYPARK |
| 210D | NAC/RCC: Telecoding_Fct_CLIM |
| 210E | NAC/RCC: Telecoding_Fct_DSG |
| 210F | NAC/RCC: Telecoding_Fct_ECRAN_PRINCIPALE |
| 2110 | NAC/RCC: Telecoding_Fct_ECRAN_SECONDAIRE |
| 2112 | NAC/RCC: Telecoding_Fct_HDC |
| 2113 | NAC/RCC: Telecoding_Fct_HY |
| 2114 | NAC/RCC: Telecoding_Fct_INTERNET |
| 2115 | NAC/RCC: Telecoding_Fct_MPD |
| 2117 | NAC/RCC: Telecoding_Fct_RADIO |
| 2118 | NAC/RCC: Telecoding_Fct_RADIO_NUM |
| 2119 | NAC/RCC: Telecoding_Fct_SAM |
| 211A | NAC/RCC: Telecoding_Fct_STT |
| 211B | NAC/RCC: Telecoding_Fct_XVV |
| 211C | NAC/RCC: Telecoding_Fct_WIFI |
| 211D | NAC/RCC: Telecoding_Fct_ASR |
| 211E | NAC/RCC: Telecoding_Fct_ADML |
| 211F | NAC/RCC: Telecoding_Fct_LANG |
| 2120 | NAC/RCC: Telecoding_Fct_LKA |
| 2121 | NAC/RCC: Telecoding_Fct_ACV |
| 2124 | NAC/RCC: Telecoding_Fct_LUM |
| 2125 | NAC/RCC: Telecoding_Fct_OBC |
| 2126 | NAC/RCC: Telecoding_Fct_CPUSH |
| 2128 | NAC/RCC: Telecoding_Fct_SPY |
| 2127 | NAC/RCC: Telecoding_Fct_IHM |
| 2116 | NAC/RCC: Telecoding_Fct_NAV |
| 0100 | NAC/RCC: Calibration_Fct_AAS |
| 0105 | NAC/RCC: Calibration_Fct_AVR |
| 0106 | NAC/RCC: Calibration_Fct_BT |
| 0107 | NAC/RCC: Calibration_Fct_BTEL |
| 010A | NAC/RCC: Calibration_Fct_CITYPARK |
| 010C | NAC/RCC: Calibration_Fct_ENTREE_VIDEO |
| 010D | NAC/RCC: Calibration_Fct_FAN |
| 010E | NAC/RCC: Calibration_Fct_FMUX |
| 010F | NAC/RCC: Calibration_Fct_HY |
| 0110 | NAC/RCC: Calibration_Fct_INTERNET |
| 0112 | NAC/RCC: Calibration_Fct_NAV |
| 0115 | NAC/RCC: Calibration_Fct_STT |
| 0116 | NAC/RCC: Calibration_Fct_XVV |
| 0117 | NAC/RCC: Calibration_Fct_LUM |
| 011A | NAC/RCC: Calibration_Fct_WIFI |
| 0119 | NAC/RCC: Calibration_Fct_LANG |
| 0118 | NAC/RCC: Calibration_Fct_OBC |
| 011B | NAC/RCC: Calibration_Fct_VIDEOTIMING |
| 011E | NAC/RCC: Calibration_Fct_SVR |
| 2123 | NAC/RCC: Telecoding_Fct_Alarm_2 |
| 0103 | NAC/RCC: Calibration_Fct_AUDIO |
| 2129 | NAC/RCC: Telecoding_Fct_LVDS |
| 2105 | NAC/RCC: Telecoding_Fct_AVP |
| 212A | NAC/RCC: Telecoding_Fct_VISIOPARK |
| 0120 | NAC/RCC: Calibration_Fct_VISIOPARK |
| FFF1 | NAC/RCC: Calibration_Fct_COLOR_CORRECTION |
| 011D | NAC/RCC: Calibration_Fct_HDC |
| 011F | NAC/RCC: Calibration_Fct_LVDS |
| 212C | NAC/RCC: Telecoding_Fct_ION |
| 212D | NAC/RCC: Telecoding_Fct_PPS |
| 212E | NAC/RCC: Telecoding_Fct_IDVR |
| 212F | NAC/RCC: Telecoding_Fct_AUDIO2 |
| 2130 | NAC/RCC: Telecoding_Fct_BTA |
| 0104 | NAC/RCC: Calibration_Fct_AVP |
| 011C | NAC/RCC: Calibration_Fct_CLIM |
| 0121 | NAC/RCC: Calibration_Fct_ION |
| 0122 | NAC/RCC: Calibration_Fct_PPS |
| 2131 | NAC/RCC: Telecoding_Fct_ANDROID |
| 2132 | NAC/RCC: Telecoding_Fct_IDVR_HMI |
| 0123 | NAC/RCC: Calibration_Fct_VIDEOTIMING_2 |
| 2133 | NAC/RCC: Telecoding_Fct_WAVE3 |
| 0124 | NAC/RCC: Calibration_Fct_LVDS_EXPORT |
| 0125 | NAC/RCC: Calibration_Fct_HW_VERSION |
| 0126 | NAC/RCC: Calibration_Fct_BEIDOU |
| 0127 | NAC/RCC: Calibration_Fct_DGT |
| 0128 | NAC/RCC: Calibration_Fct_MASS |
| 0129 | NAC/RCC: Calibration_Fct_PPS2 |
| 012A | NAC/RCC: Calibration_Fct_VP1_HW |
| 012B | NAC/RCC: Calibration_Fct_USB |
| 00DE | NAC/RCC: Calibration_Fct_PUSH_LUM |
| 00DD | NAC/RCC: Calibration_Fct_AEE_SEL |
| 2145 | NAC/RCC: Telecoding_Fct_AIO |

## Diagnostic frames explanation / What the Sketch is doing

CAN-BUS is limited to 8 bytes per frame, to send larger data PSA chose a simple algorythm to truncate the data into multiple parts

### To send data smaller or equal to 7 bytes:
#### [SEND] Frame:
| Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|--|--|--|--|--|--|--|--|
| Full Data Length | Data[0] | Data[1] | Data[2] | Data[3] | Data[4] | Data[5] | Data[6] |

### To send data larger than 7 bytes:
#### [SEND] First Frame:
| Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|--|--|--|--|--|--|--|--|
| 0x10 | Full Data Length | Data[0] | Data[1] | Data[2] | Data[3] | Data[4] | Data[5] |
#### [RECEIVE] Write Acknowledgement Frame:
| Byte 1 | Byte 2 | Byte 3 |
|--|--|--|
| 0x30 | 0x00 | 0x0A |
#### [SEND] Second Frame:
##### ID starting at 0x21 and increasing by 1 for every extra frame needed, after 0x2F reverting back to 0x20
| Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|--|--|--|--|--|--|--|--|
| 0x21 | Data[6] | Data[7] | Data[8] | Data[9] | Data[10] | Data[11] | Data[12] |
#### [SEND] Third Frame:
| Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|--|--|--|--|--|--|--|--|
| 0x22 | Data[13] | Data[14] | Data[15] | Data[16] | Data[17] | Data[18] | Data[19] |

### To receive data smaller or equal to 7 bytes:
#### [RECEIVE] Frame:
| Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|--|--|--|--|--|--|--|--|
| Full Data Length | Data[0] | Data[1] | Data[2] | Data[3] | Data[4] | Data[5] | Data[6] |

### To receive data larger than 7 bytes:
#### [RECEIVE] First Frame:
| Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|--|--|--|--|--|--|--|--|
| 0x10 | Full Data Length | Data[0] | Data[1] | Data[2] | Data[3] | Data[4] | Data[5] |
#### [SEND] Read Acknowledgement Frame:
| Byte 1 | Byte 2 | Byte 3 |
|--|--|--|
| 0x30 | 0x00 | 0x05 |
#### [SEND] Second Frame:
##### ID starting at 0x21 and increasing by 1 for every extra frame needed, after 0x2F reverting back to 0x20
| Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|--|--|--|--|--|--|--|--|
| 0x21 | Data[6] | Data[7] | Data[8] | Data[9] | Data[10] | Data[11] | Data[12] |
#### [SEND] Third Frame:
| Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 |
|--|--|--|--|--|--|--|--|
| 0x22 | Data[13] | Data[14] | Data[15] | Data[16] | Data[17] | Data[18] | Data[19] |

> Received frames could be out-of-order, ID must be used to append parts at the correct position into the final data whose size is known

## Calibration file (.cal) explanation

Every line of calibration files has this form:

### Content Size
| TYPE | LENGTH | ADDRESS | LENGTH2 | ZONE | DATA | CHECKSUM | CHECKSUM2 |
|--|--|--|--|--|--|--|--|
| 1h | 1h | Variable Length | 1h | 2h | Variable Length | 2h| 1h |

1h = 1 HEX Byte or 2 characters in the .cal file

### Content Data
| Line Part | Line Detail |
|--|--|
| **TYPE** | S1 = ZI Zone / S2 / S8 |
| **LENGTH** | Hex Length of ADDRESS+ZONE+DATA+CHECKSUM+CHECKSUM2 |
| **ADDRESS** |  |
| **LENGTH2** | Hex Length of ZONE+DATA+CHECKSUM  |
| **ZONE** |  |
| **DATA** |   |
| **CHECKSUM** | *CRC-16/X-25*(DATA) with this order CRC[1] CRC[0] |
| **CHECKSUM2** | *CRC-8/2s_complement*(ADDRESS+ZONE+DATA+CHECKSUM) - 1 |