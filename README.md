![Alt text](pics/rpi-WeMo_Logo.png?raw=true "rpi-WeMo logo")

rpi-WeMo
===============
Setting up your Raspberry Pi GPIO's to be controlled with *Amazon Alexa* using the *WeMo Emulation Server*
_____________________________________________

## 1- Install the alexa-raspberry (WeMo Emulation Server for Alexa)

### Install npm at the Pi
```
$ sudo apt-get install npm
```

### Install the alexa-raspberry npm
```
$ sudo npm install alexa-raspberry -g
```
_____________________________________________
## 2 - Clone this repository
```
$ git clone https://github.com/fejao/rpi-WeMo.git
```
_____________________________________________
## 3 - Set your LED's
Here are the schematics that I used to set my one.

![Alt text](pics/WeMo_01_bb.png?raw=true "Raspberry Connections 1")

The GPIO's that I'm using is:

**17** Yellow LED

**18** Blue LED

**22** Red LED

**23** Green LED

![Alt text](pics/GPIO_pins_output.png?raw=true "Raspberry Connections 2")

_____________________________________________
## 4 - Customizing

The script can have such input:
### gpio-set.py Script
```
$ ./gpio-set.py [-h] [-v] [-s SET_LED] [-g GPIO_NUM] [-c COLOR_NAME]
```

With optional arguments:

*  **-h, --help**
  * show help message and exit
*  **-v, --verbose**
  * increase output verbosity
*  **-s SET_LED, --set-led SET_LED**
  * Set the LED ('on', 'off'), default: off
*  **-g GPIO_NUM, --gpio-num GPIO_NUM**
  * Number for the GPIO input, default: 18
*  **-c COLOR_NAME, --color-name COLOR_NAME**
  * Color name: 'blue', 'green', 'red' and 'yellow'

The default *GPIO* is set to be use the **18**, you can change this at the script over the *global variable* **DEFAULT_GPIO**

```
DEFAULT_GPIO = <YOUR_DEFAULT_GPIO>
```

For example to turn on the **17** GPIO you should run:
```
$ ./gpio-set.py -s on -g 17
```

### wemo-devices.json File

Feel free to use different *GPIO's*, just don't forget to update the **devices.json** file and change from:
You can change the file to use your own command:

```
"<YOUR_COMMAND_NAME_HERE>":{
  "oncommand": "./gpio-set.py -s on -g <YOUR_GPIO_NUMBER> -v"
  "oncommand": "./gpio-set.py -s off -g <YOUR_GPIO_NUMBER> -v"
}
```

For example, to use the command as **Test LED** using the **22** GPIO you should use as:
```
"Test LED":{
  "oncommand": "./gpio-set.py -s on -g 22 -v"
  "oncommand": "./gpio-set.py -s off -g 22 -v"
}
```

_____________________________________________
## 4 - Start the Server
```
$ cd rpi-WeMo
$ alexa-raspberry wemo-devices.json
```
_____________________________________________
## 5 - Add devices to Alexa
Just ask *Alexa* it to look for new devices, like:
**Alexa, search for devices**

_____________________________________________
## 6 - Use it
Set the command to *Alexa*:
**Alexa, turn on Blue LED**

_____________________________________________
## 7 - Video using it
Sorry for my german *:P*

[![Alt text](https://img.youtube.com/vi/9fiR6n89Ilc/0.jpg)](https://www.youtube.com/watch?v=9fiR6n89Ilc)
