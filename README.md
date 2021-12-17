# esp_micropython
Micropython auf einen ESP32 installieren



## Herunterladen von Micropython
Diese Binäre Datei ist eine Version für ein ESP32-CAM und enthält auch das camera Modul

https://github.com/lemariva/micropython-camera-driver/blob/master/firmware/micropython_cmake_9fef1c0bd_esp32_idf4.x_ble_camera.bin

## Installieren von ESP-Tools
```console
pip3 install esptool
```

## ESP vorbereiten und löschen
```console
esptool.py --port /dev/tty.usbserial erase_flash
```


## ESP mit Micropython flsashen
```console
esptool.py --chip esp32 --port /dev/tty.usbserial --baud 460800 write_flash -z 0x1000 micropython_cmake_9fef1c0bd_esp32_idf4.x_ble_camera.bin
```


## Foto erzeugen
```python
import camera

camera.init(0)
picture = camera.capture()

picfile = open("picture.jpeg", "wb")
picfile.write(picture)
picfile.close()
```
