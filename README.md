# Water Depth Meter
ESPhome project to montior water depth and air humidity

## Background
Various recurring damp problems under my house, due to drainage problems (now fixed) and high water table.  Ultimately this required two sump pumps to remove water.
On an ongoing basis, I wanted to measure and log water depth in the sumps, as well as ambient humidty and temperature.

## Concept
Wifi connected water depth meter using ultrasonic transducer and humidity sensor with local display.
 - ESP32 to control everything
 - Low cost ST7789V 1.14" TFT display
 - DHT11 Temperature/humidty sensor
 - JSN20 depth sensing circuit (used in car reversing sensor)
 - Custom 3D printed two part housing
 - All mounted inside a standard piece of 50mm OD polycarbonate tube (length of tube can be adjusted to change overall sensing depth).
 - Ultrasonic sensor 'looks' down the tube.
 - USB cable enters through the top of the housing, and provides power.  Also provides facility to communicate with the ESP and re-flash the firmware if the OTA update breaks for whatever reason.
 - Onboard display shows all sensor readings, as well as wifi signal strength (helpful when initially installing or verifying).



This is an enhanced version of a simpler device I produced previously, which had just the JSN20 sensor mounted into a piece of drainpipe, all controlled by a raspberry Pi.


