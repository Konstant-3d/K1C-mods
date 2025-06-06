# K1C-mods
My modifications of K1C Klipper 

## Nozzle mcu temperature

Installation:
 - upload file `/usr/share/klipper/klippy/extras/temperature_mcu.py` to printer
 - delete temperature_mcu.pyc in target directory
 - reboot printer

Add folowing section to printer.cfg

    [temperature_sensor nozzle_mcu_temp]
    sensor_type: temperature_mcu
    sensor_mcu: nozzle_mcu
    min_temp: 0
    max_temp: 100
