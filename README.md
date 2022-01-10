
# signalk-raspberry-pi-bmp180
UNDER TEST!
bmp180 temperature and pressure sensor information for SignalK (SK).
This plugin can be downloaded via the SignalK application.
This plugin has been inspired by the plugin "signalk-raspberry-pi-bme280" developped by Jeremy Carter.

## Getting Started
You will need a raspberry pi with SignalK installed along with a bmp180 sensor.

### The BMP180 sensor
Personally I am using the sensor found at the following link on Amazon. However there are many manufacturers to pick from.
HiLetgo bmp180 Environmental Sensor Sensing Environmental Temperature and barometric Pressure for Raspberry Pi Arduino STM32 I2C and SPI Interfaces
by Bosch.

Learn more: https://www.amazon.com/HiLetgo-Digital-Barometric-Pressure-Replace/dp/B01F527EXS/

The datasheet of the bmp180 can be found here: https://cdn-shop.adafruit.com/datasheets/BST-BMP180-DS000-09.pdf

### Connecting the Sensor
All you need is connecting the 4 pins (3.3V Power - VCC), (I2C - SDA), (I2C - SCL) and (Ground - GND) to your Raspberry Pi.

The GPIO of the raspberry Pi is detailed here: https://docs.microsoft.com/pt-br/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi

You need to make sure Raspberry Pi is turned off while doing this!

In order to use the sensor, the i2c bus must be enabled on your rasbperry pi. This can be accomplished using "sudo raspi-config".

## Troubleshooting
When you first start SK, you should see one of two things in the /var/log/syslog; bmp180 initialization succeeded or bmp180 initialization failed along with details of the failure.

If the sensor isn't found you can run `ls /dev/*i2c*` which should return `/dev/i2c-1`. If it doesnt return then make sure that the i2c bus is enabled using raspi-config.

You can also download the i2c-tools by running `sudo apt-get install -y i2c-tools`. Once those are installed you can run `i2cdetect -y 1`. You should see the bmp180 detected as address 0x77. If the sensor isn't detected then go back and check the sensor wiring.

## Authors
* **Jean-David Caprace** - *Author of this plugin*
