# QS-WIFI-D02-TRIAC-2C
Conversion of QS-WIFI-D02-TRIA-2C Tuya based dimmer to Tasmota fw.
The device is MOSFET based not TRIAC as stated by device name.

## Install TASMOTA
Flashing of ESP8266 (LM1) can be done through [Tuya-Convert](https://tasmota.github.io/docs/Tuya-OTA), but future update could fix it. It is always possible to flash it via serial (remembering to disable the two STM mcu chip connecting EN pins to GND).

**REMEMBER** to flash a Tasmota build with script enabled.

## Set-Up Tasmota
### TEMPLATE:
`{"NAME":"QS-WIFI-D02","GPIO":[255,148,255,149,38,43,255,255,37,42,255,255,255],"FLAG":0,"BASE":1}`

### Console:
- Enable Multi-channel PWM (to make the color channel a second brightness channel)
`SetOption68 1`
- Update of Dimmer/Color/CT without turning power on (decouple Channel<x> and Power<x>):
`SetOption20 1`
 
 ### Script:
 Copy and paste the [Dimmer-QS-WiFi-D02-Script.txt](https://github.com/mick96/QS-WIFI-D02-TRIAC-2C/blob/master/Dimmer-QS-WiFi-D02-Script.txt)
 
## Troubleshooting
The device seems to be effected by conducted interference on SW pins. This is probably due to coupling with main 50/60Hz and the design of internal voltage divider (see [Input SW circuit](https://github.com/mick96/QS-WIFI-D02-TRIAC-2C/blob/master/SW_InternalCircuit.png)). An easy solution to this is add a 2MOmh resistance in series to each SW channels.
