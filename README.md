# Plant Tech 🌱

We're excited to have you join this course, where you'll be working with plants, Arduino boards, moisture sensors and watering systems.

The aim of Make Days is to explore and learn new thing. You don't need to achieve specific goals. The structure caters for varying levels of experience and different Makers will learn different things by playing with the same tools.

# Preparing for the Make Day

Makers that arrive well prepared get the most out of their experience. Before you attend your Make Day, there are a couple of activities to complete.

## Prep

Here's a list of things you'll need to prep before you can set up your watering system. 

- Install the [Arduino IDE](https://www.arduino.cc/en/main/software)
- Read the [Quick Start to Nodemcu (ESP8266) on Arduino IDE](https://www.instructables.com/id/Quick-Start-to-Nodemcu-ESP8266-on-Arduino-IDE/)

Important: if you want to use the ESP8266 WEB Server in this example you will need to downloand the following two libraries. These libraries are not available in the library manager.

### Installing the ESPAsyncWebServer library
The ESPAsyncWebServer library is not available to install in the Arduino 
Library Manager. So, you need to install it manually.

Follow the next steps to install the ESPAsyncWebServer library:

https://github.com/me-no-dev/ESPAsyncWebServer/archive/master.zip

Unzip the .zip folder and you should get ESPAsyncWebServer-master folder
Rename your folder from ESPAsyncWebServer-master to ESPAsyncWebServer
Move the ESPAsyncWebServer folder to your Arduino IDE installation libraries folder

### Installing the ESPAsync TCP Library
The ESPAsyncWebServer library requires the ESPAsyncTCP library to work. Follow the next steps to install that library:

https://github.com/me-no-dev/ESPAsyncTCP/archive/master.zip

Unzip the .zip folder and you should get ESPAsyncTCP-master folder
Rename your folder from ESPAsyncTCP-master to ESPAsyncTCP
Move the ESPAsyncTCP folder to your Arduino IDE installation libraries folder
Finally, re-open your Arduino IDE

You may also need [the driver](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers) for the usb-uart

# What will be available for you on the evening

* ESP8266 module
* Dopunt f-f wires (x10)
* Moisture sensor
* Micro usb to usb A cable
* Watering pump
* PVC tube + cable tie
* TIP31C Transistor

# Bring your own:

* Tall glass or container with water to test the sensor and water pump
* Laptop/PC with USB-A port

# How to get started

## Pinouts
ESP8266:

<img src="https://i2.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/05/ESP8266-NodeMCU-kit-12-E-pinout-gpio-pin.png?ssl=1" alt="ESP8266" width="250"/>

Mini Submersible 5V Water Pump:

<img src="https://potentiallabs.com/cart/image/cache/catalog/New%20Components-17/Mini%20Waterpump-800x800.png" alt="pump" width="250"/>

TIP31C (NPN) Transistor:

<img src="https://www.componentsinfo.com/wp-content/uploads/2020/08/tip31c-pinout-equivalent.gif" alt="tip31c" width="250"/>

Moisture Sensor:

<img src="https://components101.com/sites/default/files/component_pin/Moisture-Sensor-Module-Pinout.jpg" alt="moisture" width="250"/>

## Part 1 - Set up your plant!

Add 300 ml water to the bag with pressed soil, forming ~1 liter of compost. Make a few small holes in the soil and place the basil seeds in them, covering with a bit of loose soil.

## Part 2 - Moisture Sensor

Connect the moisture sensor with the LM393 chip (). The sensor has both an analog (0 for wet and 1023 for dry) and a digital (LOW for wet and HIGH for dry) output. Check the pinout for the sensor above and see where it would connect to the ESP8266 board (it has a A0, D0, GND, and needs a voltage).

Connect the ESP8266 with your PC and start up the Android IDE. Try getting the sensor up and running to print its moisture values (analog is more interesting here as it gives you a value from a wetness-range). If coding isn't your strong suit, you can use the code provided in this repo for the [Moisture Sensor](https://github.com/OfferZen-Make/plant_tech_ams/blob/master/MoistureSensor.ino).

Upload your code to your system (cntrl-U / cmd-U), wait untill the upload is done - the terminal should read: "Leaving... Hard resetting via RTS pin..." - and open the monitor (Tools > Serial Monitor) to see your printed values.

Put your sensor (only the two large exposed pads) in the compost of your plant, or simply put it in a glass of water, to do some readings!

### Troubleshooting

- Sometimes the ESP8266 does not show in your IDE. If so, look for the right USB-port (Tools > Port).
- Select the 115200 BAUD option for upload speed, otherwise your readings are not properly displayed.

## Part 3 - Mini Water Pump

The pump is water submersible, sucks in water from the hole on the opposite end of the wires, and pumps it through the little outlet. In order to switch the pump on and off, it needs to be connected to the ESP8266 with the TIP31C Transistor.

The pump has a GND output to be connected to the ESP8266 and receives power from the emitter pin of the transistor. The transistor gets it power through its collector pin from the ESP8266's 3V3 pin. Finally, connect the base to the D1 pin to be able to control the pump.

Write some code (or check the code from the [complete watering system](https://github.com/OfferZen-Make/plant_tech_ams/blob/master/plant_watering_system.ino) in this repo) to get the pump up and running. Before uploading the code, make sure to submerse the pump in your tall glass/container filled with water, as you do not want to overheat its motor - and watch out for water spills ;)

## Part 4 - Time to play!

Now that the basics of your system are up and running, it's time to play around a bit. You can put your moisture sensor in your plant and attach the PVC tubing to the water pump (potentially use the cable tie to prevent leaking) with one end, and lay the other end in the plant.

See what analog value would be a good threshhold of dryness. Implement this in your code to start activating your pump as soon as this threshold is reached. Also try to implement some delays in your code to stop the pump after a few seconds, as it takes some time for the soil to get moist and the sensor to pick this up.

If you are confident that your very own automated watering system is fully working, you can check out the repos below for some inspiration on how to communicate with your system via your phone :)

### Further ideas
- Let your system update you via text on when to water your plants with the [MessageBird API](https://developers.messagebird.com/quickstarts/sms/send-sms-curl/)
- Telling your plant to water itself - by speech! [Blogpost + code](https://codeburst.io/home-automation-using-google-assistant-dialogflow-firebase-esp8266-wemos-part-1-800c4dc15ad9)

#### Sources
- [Soil Moisture Sensor Tutorial for Arduino, ESP8266 and ESP32](https://diyi0t.com/soil-moisture-sensor-tutorial-for-arduino-and-esp8266/)
- [Soil Moisture Sensor Setup for Arduino](https://www.instructables.com/id/Arduino-Soil-Moisture-Sensor/)
- [ESP8266 smart plant irrigation system](https://iot-playground.com/blog/2-uncategorised/94-esp8266-smart-plant-irrigation-system)

# Useful resources
- [ ] Check out the [OfferZen Make Subreddit](https://www.reddit.com/r/offerzenmake) and upvote any answers you find useful. Feel free to add your own questions and comments! 
- [ ] Join Make Slack, introduce yourself in #meet-and-greet, and check in with your team channel
- [ ] Learn about the how, where and why of Make Days with the [Make Manifesto](https://docs.google.com/document/d/12OtTltO-ozhGd7OzDswgLoRMLtfd3_i8_Pxw1Dx551U/edit)

* Know somebody who would enjoy this course? Share their names with us and we'll send a Make @ Home Box their way!
