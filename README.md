# ESB Fitness

## What is & How it works
ESB Fitness is an easy script to help your home-fitness. Once loaded to ESP8622 board, it counts how many time you complete your flight/flights of stairs and sends you a notification when you reach a defined goal. Put the sensor on the top or bottom of the stairs, so it counts a full up&down flight/flights
The default target is 1576 stairs which stands for the Empire State Building 86-flights distance. This is the reason of the "ESB" name :)
I've created it to make some fitness at home during the lockdown and found it pretty challenging.
It needs to be uploaded to an ESP8266 board (I've tested it on a Wemos D1 Mini Pro) connected to a HC-SR04 distance sensor.
You need to upload the script using the Arduino IDE with some libraries installed: Universal Arduino Telegram Bot and the Benoît Blanchon's ArduinoJson library.

I've used parts of code from other projects/tutorial I've found online but I really don't remember the sources. If you are an author and want to be credited just contact me.

## What I need
- ESP8266 board (tested on a Wemos D1 Mini Pro)
- HC-SR04 distance sensor (Connect the sensor to the board as follows)
    - GND -> GND
    - ECHO -> D7
    - TRIG -> D6
    - VCC -> 5V
- Universal Arduino Telegram Bot library (install in the Arduino IDE from here: https://github.com/witnessmenow/Universal-Arduino-Telegram-Bot)
- Benoît Blanchon's ArduinoJson library (install in the Arduino IDE from Library Manager -> Search for __ArduinoJson__ by Benoît Blanchon)
- A Telegram Bot and a Chat ID (If you don't have one, you can find many easy tutorials on the web)

Change the default values and copy the source code to a new Arduino script and upload it to the board.

## How to change the default values
There is a dedicated part on the top of the script called __VALUES YOU NEED TO CHANGE__.
You have to change the **bold** parts to make it work:

const char* ssid     = "**WIFI_Network_Name**";            //Name of your WiFi network <br>
const char* password = "**WIFI_Network_Passw**";  // Password of your WiFi network<br>
#define BOT_TOKEN "**XXXXXXXXX:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX**" // Telegram BOT Token<br>
#define CHAT_ID "**XXXXXX**"                      // Telegram Chat ID where to send the message <br>
const int TargetStairs = **1576**;                  // Target of stairs you want to do (1576 is the Empire State Building Run-Up distance)<br>
const int YourStairs = **52**;                      // Consecutive steps you have in the stairs you want to use (uphill)<br>
const int MaxDist = **80**;                         // Maximum distance of an object (in cm) to count the passage in front of the sensor<br>
const int DelayAfterPass = **15**;                   // Seconds of sleep after counting a passage (to avoid multiple passes in few seconds)<br>

Just modify these values and everything else should work fine.
**Please note that I've set a default 10 seconds delay after connecting the board to the power before the board starts counting**

## Updates will follow?
Yes, I'm planning to add a time-count feature that let you know in how much time you reached the goal so you can compare the performance every day. I'm also planning to add a mid-distance notification and possibly some interaction via the Telegram chat you use (manual start, pause/restart, set time targets).
If you are able to implement this features I'm happy to receive some help!
