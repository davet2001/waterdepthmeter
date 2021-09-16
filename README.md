# Water Depth Meter
ESPhome project to montior sump water depth and air humidity.

## Background
Various recurring damp problems under my house, due to drainage problems (now fixed) and high water table.  Ultimately this required two sump pumps to remove water.
On an ongoing basis, I wanted to measure and log water depth in the sumps, as well as ambient humidity and temperature.  Mainly for fun, I decided to go for a semi professional looking device, with a clean look and high build quality.  I also wanted to try out some 3D printing.

## Concept
![image](https://user-images.githubusercontent.com/17680170/133689217-e998cfe9-9e51-48ec-9eaf-b2c0c8456f52.png)

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
 - FreeCAD for the mechanical parts and assembly4 addon for the assembly model.  I was able to find existing 3D models (stp files) of each of the electronic modules, so didn't need to model them myself.  FreeCAD is good but the assembly editor is infuriating (fragile models, where constraints and links keep moving by themselves).
 - GIMP for the display design
 - ESPHome for the ESP32 code.
 - craftcloud3d.com for the 3D printed parts (first time using them).
 - Aliexpress for the electronics.
 
This is an enhanced version of a simpler device I produced previously, which had just the JSN20 sensor mounted into a piece of drainpipe, all controlled by a raspberry Pi.

## Build
The parts assembled quite well, some small modificaitons were needed to the 3D printed parts.  Holes were drilled in the tube to allow water in/out.

![image](https://user-images.githubusercontent.com/17680170/133689550-6ed1274e-bd1f-48fc-83d4-1712ba2db530.png)
![image](https://user-images.githubusercontent.com/17680170/133689632-899e34ca-bf16-4ba9-b58a-0ccef6238a78.png)

A small amount of silicone sealant was used to make the DHT11 cable route watertight
![image](https://user-images.githubusercontent.com/17680170/133690171-add86631-1e3b-45a2-b2c8-7b06275f504d.png)


## Initial testing and modifications.
On first run, the temperature/humidity sensor, wifi and screen, were all working well but the depth sensor was reporting NaN on the screen meaning no valid measurement.  After testing the ultrasonic sensor in several ways unsuccessfully, I decided it was faulty and replaced it.  The new one worked ok when outside of the housing but did not work inside the tube.

## Optimisations
I had the idea that there might be an echo from the inside of the tube, so I set about trying to eliminate this.  By trial and error with a bit of experimentation, I eventually settled on a tube of felt approx 100mm long, fitted round the inside top of the tube just below the sensor.  This made a huge difference - the readings were consistent and reliable.

In the esphome configuration, I corrected for the length of the tube, so that it would report zero when the water level was at the end of the tube, and positive values as the water rose up the tube.
![image](https://user-images.githubusercontent.com/17680170/133690247-a0712b80-1677-4d61-aa93-31492c256fc4.png)

## What I would change next time
 - Slightly adjust the dimensions of the lid so that it fits properly.
 - Taper one end of the lid so that it can be assembled (if you are reproducing this design - don't worrry, some small modificaitons with a knife/sandpaper are enough to resolve this).
 - The O-rings were ineffective as they didn't sit in the groove properly - this was mostly because I couldn't get the correct size.  In the end the device formed quite a good seal so the o-rings were not so critical.
 - Come up with a more secure method of fastenning the screen (the pegs aligned it well, but two of them broke and there wan't anything to hold the screen down).

## Overall 

Successful project!  I am pleased with the final result.


https://user-images.githubusercontent.com/17680170/133690893-c571fd80-702e-4a02-8ebf-a6f5f6914e51.mp4

