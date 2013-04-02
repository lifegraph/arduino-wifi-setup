# How to get an Arduino connected to the internet using WiFly and Lifegraph

**What you'll learn:** 
* How to correctly set up and solder your WiFly module
* How to install the Arduino libraries for WiFlyHQ and Lifegraph
* How to get your Arduino talking to the internet by making an example GET request

**What you'll need:**
* [An Arduino](https://www.sparkfun.com/products/11021) ($30)
* [A WiFly Module](https://www.sparkfun.com/products/10822) ($35)
* A Wifi network to connect to
* Strength of a tiger

If you've never touched an Arduino, make sure you've [set up your Arduino environment](http://arduino.cc/en/Guide/HomePage)!

Let's do it!

## Soldering the WiFly (XBee form factor)

There are 4 pins that you need to connect from the WiFly module to the Arduino: 3.3v, GND, TX (for transmitting), and RX (for receiving).

These 4 pins correspond to the following on the WiFly module

![WiFly](https://raw.github.com/lifegraph/wifly-setup/master/imgs/wifly.png)

* Pin 1 &mdash; 3.3v. Connect this to the **3.3v pin** on the Arduino.
* Pin 2 &mdash; This is the Transmitter pin for the WiFly. Connect it to Digital pin 2 on the Arduino.
* Pin 3 &mdash; This is the Receiver pin for the WiFly. Connect it to Digital pin 3 on the Arduino.
* Pin 10 &mdash; Connect this to GND.

We recommend using [male to male header pins](https://www.sparkfun.com/products/116) because the WiFly is rather small and soldering directly pin to pin can be frustrating. 
Note that after soldering and connecting to the Arduino, if everything is correct, a red light will blink on the WiFly. 

![WiFly all wired up](http://i.imgur.com/EDxmchO.png)

Awesome job! Now we have the hardware set up, let's set up the software libraries.

## Installing the WiFlyHQ and Lifegraph Arduino Libraries

**We'll be using:**
* [WiFlyHQ](https://github.com/harlequin-tech/WiFlyHQ) for interfacing with the WiFly module
* [Lifegraph](https://github.com/lifegraph/arduino-lifegraph) for making http calls easily

In order to setup the WiFlyHQ and Lifegraph Arduino Libraries, you'll need to download them both from github to your Arduino libraries folder. You can do this with git or without!

**With Git:**
If you have git, clone the WiFlyHQ repository and the Lifegraph repository into your Arduino libraries directory. On OSX this is typically in `~/Documents/Arduino/libaries/`. If you don't have a libraries folder, you'll need to make one.
```
cd ~/Documents/Arduino/libraries
git clone https://github.com/harlequin-tech/WiFlyHQ
git clone https://github.com/lifegraph/arduino-lifegraph Lifegraph
```

**Without Git:**
Go to [WiFlyHQ](https://github.com/harlequin-tech/WiFlyHQ/archive/master.zip) to download a zip file of the directory, then extract the files into your Arduino libraries folder. On OSX this is typically in `~/Documents/Arduino/libaries/`. If you don't have a libraries folder, you'll need to make one. Then go to [Lifegraph](https://github.com/lifegraph/arduino-lifegraph/archive/master.zip) to download a zip file of the directory, and again extract the files into your Arduino libraries folder.

The finished libraries folder should have a WiFlyHQ folder and an arduino-lifegraph folder.

![Arduino Libraries all installed in the Arduino/libraries directory](https://raw.github.com/lifegraph/wifly-setup/master/imgs/libraries_installed.png)

## Time to talk to the internet.

After you add the library, you'll need to restart the Arduino IDE for it to pick up the library. If you've added it in the right place, you should be able to see the WiFlyHQ and Lifegraph library if you go to Sketch -> Import Library.

After you have the library working, open up a new sketch in your Arduino environment, and copy the code for the [httpclient example](https://github.com/lifegraph/wifly-setup/blob/master/httpclient/httpclient.ino).  

In `httpclient.ino`, you'll need to change the SSID (name of your network) and the password to work with your own WiFi network:

```ino
const char mySSID[] = "your_ssid";
const char myPassword[] = "your_password";
```

The next step is to fill in the appropriate post URL, host, and content type in `httpclient.ino`. For example, if you were doing the [Graph Button](https://github.com/lifegraph/graphbutton-wifly.git) tutorial, those fields might look something like: 

```ino
wifly.println("POST /action/60ce6bdda1e131973c722d0906524b2ed24c44a6 HTTP/1.1");
wifly.println("Host: graphbutton.herokuapp.com:80");
wifly.println("Content-type: application/json");
```

However, you can configure `httpclient.ino` to point to any action or app you create. 

## Want to learn more? 

[Lifegraph Labs](http://www.lifegraphlabs.com) has [Tutorials](http://lifegraphlabs.com/how-to) to connect the real world with the digital, [Tools](http://lifegraphlabs.com/tools) to get you started quickly, and [Ideas](http://lifegraphlabs.com/ideas) of awesome things you could build right now. [Go there now!](http://www.lifegraphlabs.com) 

