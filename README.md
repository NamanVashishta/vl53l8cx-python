# vl53l8cx-python

Python ctypes wrapper for the VL53L8CX Time-of-Flight 8x8 ranging sensor on Raspberry Pi.

## Why Does This Exist?

No pip-installable Python driver exists for the VL53L8CX on Raspberry Pi. All VL53L5CX-based wrappers fail due to firmware blob incompatibility. This library wraps the official VL53L8CX Ultra Lite Driver (ULD) C source using Python ctypes. First working Python driver for this sensor on Linux/Raspberry Pi.

Tested on: Raspberry Pi Zero 2 W, Raspberry Pi OS Bookworm 64-bit, Python 3.11.

## Hardware

- Pololu VL53L8CX Carrier (Product 3419) or equivalent breakout
- Wiring: VIN to 3.3V, GND to GND, SDA to Pi Pin 3, SCL to Pi Pin 5
- Pull SPI/I2C mode pin LOW to enable I2C mode

Enable I2C: sudo raspi-config nonint do_i2c 0

## Installation

    git clone https://github.com/NamanVashishta/vl53l8cx-python
    cd vl53l8cx-python/library
    python3 setup.py build_ext --inplace

## Quick Start

    from vl53l8cx_ctypes import VL53L8CX, RESOLUTION_8X8
    sensor = VL53L8CX()
    print(sensor.is_alive())  # True
    sensor.set_resolution(RESOLUTION_8X8)
    sensor.start_ranging()

## Live ASCII Stream

    python3 examples/stream.py

## Attribution

- ST VL53L8CX ULD: https://github.com/ST-mirror/VL53L8CX_ULD_driver
- Inspired by pimoroni/vl53l5cx-python (MIT)

## License

MIT
