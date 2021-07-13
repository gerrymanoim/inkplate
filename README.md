
# Flashing Steps

- Create a new conda env, pip install esptool
- wget esp32 firmware
- add myself to dialout group so I can talk to `/dev/ttyUSB0`
    - `sudo usermod -a -G dialout $USER`
    - reboot (no not logout)
- Turn on the device
- `sudo usermod -a -G dialout $USER
- `esptool.py --chip esp32 --port /dev/ttyUSB0 erase_flash`
- `esptool.py --chip esp32 --port /dev/ttyUSB0 write_flash -z 0x1000 esp32spiram-20210623-v1.16.bin`

# Other General setup

- Copy `pyboard` from tools/micropython to bin
- From the main inkplate micropython repo copy

```
gfx_standard_font_01.py
gfx.py
image.py
inkplate10.py
mcp23017.py
sdcard.py
shapes.py
```

Then

```
python ../bin/pyboard.py --device /dev/ttyUSB0 -f cp mcp23017.py sdcard.py inkplate10.py shapes.py gfx.py gfx_standard_font_01.py :
```

# Running code on the device

```
python ../bin/pyboard.py --device /dev/ttyUSB0 -f cp mcp23017.py sdcard.py inkplate10.py image.py gfx.py gfx_standard_font_01.py :
```

# Important Links

- [Inkplate Docs](https://inkplate.readthedocs.io/en/latest/index.html)
- [Inkplate Micro](https://github.com/e-radionicacom/Inkplate-micropython)
- [MicroPython ESP32](http://docs.micropython.org/en/latest/esp32/quickref.html)

# Todo

- [ ] Set up much better tooling around managing all this.
- [ ] See if I can setup https://github.com/Josverl/micropython-stubber
