#WiFlySetup, a tutorial for getting your WiFly shield up and running

This tutorial is wrtten for setting up a [Sparkfun WiFly Module ($35)](https://www.sparkfun.com/products/10822). 

**What you'll learn:** How to correctly set up your WiFly shield, in order to get your Arduino talking to the internet.

**What you'll need:**
* [A WiFly Module](https://www.sparkfun.com/products/10822) ($35)
* [An Arduino](https://www.sparkfun.com/products/11021) ($30)

## Soldering the WiFly (XBee form factor)

There are 4 pins that you need to connect from the WiFly module to the Arduino: 3.3v, GND, TX (for transmitting), and RX (for receiving).

These 4 pins correspond to the following on the WiFly module

![WiFly](https://raw.github.com/lifegraph/graphbutton-wifly/master/imgs/wifly.png)

* Pin 1 &mdash; 3.3v. Connect this to the **3.3v pin** on the Arduino.
* Pin 2 &mdash; This is the Transmitter pin for the WiFly. Connect it to Digital pin 2 on the Arduino.
* Pin 3 &mdash; This is the Receiver pin for the WiFly. Connect it to Digital pin 3 on the Arduino.
* Pin 10 &mdash; Connect this to GND.

We recommend using female to female header pins because the WiFly is rather small and soldering directly pin to pin can be frustrating. 
Note that after soldering, if everything is correct, a red light will blink on the WiFly. 

![WiFly all wired up](http://i.imgur.com/EDxmchO.png)

## Making HTTP Requests

We'll be using [WiFlyHQ](https://github.com/harlequin-tech/WiFlyHQ) as our library for interfacing with the WiFly module. This allows us to talk to the WiFly over serial.

In order to setup WiFlyHQ, you'll need to download it to your Arduino libaries. To do this, go to [WiFlyHQ](https://github.com/harlequin-tech/WiFlyHQ), click on the
"zip" button to download a zip file of the directory, then extract the files into your Arduino libraries folder. On OSX this is typically in `~/Documents/Arduino/libaries/`. If you don't have a library folder, you'll need to make one. 

```
cd ~/Documents/Arduino/libraries;
git clone https://github.com/harlequin-tech/WiFlyHQ;
```

After you add the library, you'll need to restart the Arduino IDE for it to pick up the library. If you've added it in the right place, you should be able to see the WiFlyHQ library if you go to Sketch -> Import Library.

After you have the library working, open up a new sketch in your Arduino environment, and copy the code for the [httpclient example in this repo](https://raw.github.com/lifegraph/graphbutton-wifly/master/httpclient/httpclient.ino).  

In `httpclient.ino`, you'll need to change the SSID (name of your network) and the password to work with your own WiFi network:

```ino
const char mySSID[] = "your_ssid";
const char myPassword[] = "your_password";
```
