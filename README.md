# :: mini-R :: 
## A Wi-Fi controlled rover-robot based on ESP8266
**mini-R** is a Wi-Fi controlled _robot-rover_ build around the [Adafruit Mini Robot Rover Chassis](https://www.adafruit.com/product/2939).

<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-08.jpg"/>
</figure>

At the heart of the project lies an [Adafruit ESP8266 Feather Huzzah](https://www.adafruit.com/product/2821) set up in _soft-AP mode_ controlled using a web-app based on the [WebSocket API](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API). The motor driver board is the [Adafruit DC Motor + Stepper FeatherWing](https://www.adafruit.com/product/2927).

**mini-R** works without the need for an Internet connection: the robot-rover creates its own Wi-Fi network and runs a web server that makes possible to control its movements.

## The logic inside mini-R
The code is written using the Arduino IDE and makes use of the standard ESP8266 libraries for creating a Wi-Fi network in soft-AP mode and for running a web server on **mini-R**.
The commands are received via the WebSocket interface and are linked to functions used to make the rover-robot move forward/backward and turn left/right.


## Controlling the rover-robot over Wi-Fi
The robot-rover runs a web server that creates an interface for controlling the **mini-R**'s movements.

<figure style="text-align: center; margin: auto">
  <img style="margin-bottom: 1em" src="https://www.idrovolante.org/img/mcu-esp8266-mini-r-09.png"/>
</figure>

The web-app is written in HTML5/CSS and is based on the [WebSocket API](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API).
The application code is written in _vanilla_-JavaScript in order to not rely on external libraries that would require an Internet connection or a file system build inside the ESP8266 (e.g. the SPIFFS file system).
To control the robot is as simple as using a browser connected to the IP address 192.168.4.1.
