# K1C-mods
Модификации Клиппера для Creality K1C


> [!CAUTION]
> Все что вы делаете, вы делаете на свой страх и риск, автор доработок не несет ответственности за любые повреждения, которые могут случиться из-за использования данных модификаций.

> [!IMPORTANT]
> Перед любыми манипуляциями желательно сделать резевные копии всех изменяемых файлов.

## Nozzle mcu temperature
Показ в веб-интерфейсе клиппера температуры mcu головы.

Установка:
 - загрузить `/usr/share/klipper/klippy/extras/temperature_mcu.py` в принтер
 - удалить `/usr/share/klipper/klippy/extras/temperature_mcu.pyc`
 - перезагрузить принтер

Добавить раздел в printer.cfg

    [temperature_sensor nozzle_mcu_temp]
    sensor_type: temperature_mcu
    sensor_mcu: nozzle_mcu
    min_temp: 0
    max_temp: 100

## SweepingVibrations resonanse tester
Адаптация [нового алгоритма](https://github.com/Klipper3d/klipper/pull/6723) тестирования резонансов (голова ездит и вибрирует) от Dmitry Butyugin к версии klipper  от Creality. Проверен на K1C и K1SE.

> [!CAUTION]
> В июне 2025 замечены принтеры K1SE c прошивкой 1.3.5.11 в которой изменен файл toolhead.py, для этих принтеров вместо файла toolhead.py нужно использовать toolhead_1_3_5_11.pyc, предварительно переименовав его в toolhead.pyc

Начальные условия:
 - прошивка 1.3.3.46 (возможно заработает на других, но проверялось
   только на этой)
 - HelperScript (для снятия графика по двум осям)
 - root доступ к принтеру (для заливки файлов)

Установка:
 - Загрузить в принтер файлы:
	 - /usr/share/klipper/klippy/extras/resonance_tester.py
	 - /usr/share/klipper/klippy/extras/shaper_calibrate.py
	 - /usr/share/klipper/klippy/toolhead.py
 - Удалить на принтере:
	 - /usr/share/klipper/klippy/extras/resonance_tester.pyc
	 - /usr/share/klipper/klippy/extras/shaper_calibrate.pyc
	 - /usr/share/klipper/klippy/toolhead.pyc    
 - Перезагрузить принтер

В printer.cfg в секции [resonance_tester] заменить 
`accel_per_hz: 75` на  `accel_per_hz: 60`
После этого команды `TEST_RESONANCES AXIS=X` и `TEST_RESONANCES AXIS=Y` будут снимать резонансы по новому алгоритму, а `TEST_RESONANCES_GRAPHS` еще и графики построит.

> [!TIP]
> Если необходимо вручную конвертировать на хосте csv файлы в графики (в командной строке SSH), то так же надо заменить /usr/share/klipper/scripts/calibrate_shaper.py
