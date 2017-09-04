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

Feel free to use different *GPIO's*, just don't forget to update the **devices.json** file and change from:

```

"<YOUR_COMMAND_NAME_HERE>":{
  "oncommand": "./led-set.py -s on -g <YOUR_GPIO_NUMBER> -v"
  "oncommand": "./led-set.py -s off -g <YOUR_GPIO_NUMBER> -v"
}

```
_____________________________________________
## 4 - Start the Server
```
$ cd rpi-WeMo
$ alexa-raspberry devices.json
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
