# K1C-mods
����������� �������� ��� Creality K1C


> [!CAUTION]
> ��� ��� �� �������, �� ������� �� ���� ����� � ����, ����� ��������� �� ����� ��������������� �� ����� �����������, ������� ����� ��������� ��-�� ������������� ������ �����������.

> [!IMPORTANT]
> ����� ������ ������������� ���������� ������� �������� ����� ���� ���������� ������.

## Nozzle mcu temperature
����� � ���-���������� �������� ����������� mcu ������.

���������:
 - ��������� `/usr/share/klipper/klippy/extras/temperature_mcu.py` � �������
 - ������� `/usr/share/klipper/klippy/extras/temperature_mcu.pyc`
 - ������������� �������

�������� ������ � printer.cfg

    [temperature_sensor nozzle_mcu_temp]
    sensor_type: temperature_mcu
    sensor_mcu: nozzle_mcu
    min_temp: 0
    max_temp: 100

## SweepingVibrations resonanse tester
��������� [������ ���������](https://github.com/Klipper3d/klipper/pull/6723) ������������ ���������� (������ ����� � ���������) �� Dmitry Butyugin � ������ klipper  �� Creality. �������� �� K1C � K1SE.

> [!CAUTION]
> � ���� 2025 �������� �������� K1SE c ��������� 1.3.5.11 � ������� ������� ���� toolhead.py, ��� ���� ��������� ������ ����� toolhead.py ����� ������������ toolhead_1_3_5_11.pyc, �������������� ������������ ��� � toolhead.pyc

��������� �������:
 - �������� 1.3.3.46 (�������� ���������� �� ������, �� �����������
   ������ �� ����)
 - HelperScript (��� ������ ������� �� ���� ����)
 - root ������ � �������� (��� ������� ������)

���������:
 - ��������� � ������� �����:
	 - /usr/share/klipper/klippy/extras/resonance_tester.py
	 - /usr/share/klipper/klippy/extras/shaper_calibrate.py
	 - /usr/share/klipper/klippy/toolhead.py
 - ������� �� ��������:
	 - /usr/share/klipper/klippy/extras/resonance_tester.pyc
	 - /usr/share/klipper/klippy/extras/shaper_calibrate.pyc
	 - /usr/share/klipper/klippy/toolhead.pyc    
 - ������������� �������

� printer.cfg � ������ [resonance_tester] �������� 
`accel_per_hz: 75` ��  `accel_per_hz: 60`
����� ����� ������� `TEST_RESONANCES AXIS=X` � `TEST_RESONANCES AXIS=Y` ����� ������� ��������� �� ������ ���������, � `TEST_RESONANCES_GRAPHS` ��� � ������� ��������.

> [!TIP]
> ���� ���������� ������� �������������� �� ����� csv ����� � ������� (� ��������� ������ SSH), �� ��� �� ���� �������� /usr/share/klipper/scripts/calibrate_shaper.py
