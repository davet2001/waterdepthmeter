# Water Depth Meter
ESPhome project to montior sump water depth and air humidity.

## Background
Various recurring damp problems under my house, due to drainage problems (now fixed) and high water table.  Ultimately this required two sump pumps to remove water.
On an ongoing basis, I wanted to measure and log water depth in the sumps, as well as ambient humidity and temperature.

## Concept
Wifi connected water depth meter using ultrasonic transducer and humidity sensor with local display.
 - ESP32 to control everything, using ESP32 Devkit V1 (for easy access to pins, usb port, power regulator etc).
 - Low cost ST7789V 1.14" TFT display
 - DHT11 Temperature/humidty sensor
 - JSN-SR04T depth sensing circuit (used in car reversing sensor)
 - Custom 3D printed two part housing
 - All mounted inside a standard piece of 50mm OD polycarbonate tube (length of tube can be adjusted to change overall sensing depth).
 - Ultrasonic sensor 'looks' down the tube.
 - USB cable enters through the top of the housing, and provides power.  Also provides facility to communicate with the ESP and re-flash the firmware if the OTA update breaks for whatever reason.
 - Onboard display shows all sensor readings, as well as wifi signal strength (helpful when initially installing or verifying).

The device is intended to be semi-waterproof - at least splash proof from the water depth sensing end.  The humidity sensor is mounted on the outside.

## Development
Developed using the following:
 - FreeCAD for the mechanical parts and assembly4 addon for the assembly model.
 - GIMP for the display design
 - ESPHome for the ESP32 code.
 - craftcloud.com for the 3D printed parts (first time using them).

This is an enhanced version of a simpler device I produced previously, which had just the JSN20 sensor mounted into a piece of drainpipe, all controlled by a raspberry Pi.

## Status
This is a work in progress.  Not yet assembled or tested!



