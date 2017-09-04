# WeMo Emulation Server for setting LED's with Amazon Alexa over a Raspberry Pi

## 1- Install the alexa-raspberry (WeMo Emulation Server for Alexa)

### Install npm at the Pi
```
$ sudo apt-get install npm
```

### Install the alexa-raspberry npm
```
$ sudo npm install alexa-raspberry -g
```

### Copy the repository, or write your own json file
```
$ git clone https://github.com/amansx/alexa-raspberry.git
```

## 2 - Clone this repository
```
$ git clone https://github.com/fejao/rpi-WeMo.git
```

## 3 - Set your LED's
Here are the schematics that I used to set my one.

![Alt text](pics/WeMo_01_bb.png?raw=true "Raspberry Connections 1")

The GPIO's that I'm using is:

**17** Yellow LED
**18** Blue LED
**22** Red LED
**23** Green LED

![Alt text](pics/GPIO_pins_output.png?raw=true "Raspberry Connections 2")


## 4 - Start the Server
```
$ cd rpi-WeMo
$ alexa-raspberry devices.json
```

## 5 - Add devices to Alexa
Just ask *Alexa* it to look for new devices, like:
**Alexa, search for devices**

## 6 - Use it
Set the command to *Alexa*:
**Alexa, turn on Blue LED**

## 7 - Video

[![Alt text](https://img.youtube.com/vi/9fiR6n89Ilc/0.jpg)](https://www.youtube.com/watch?v=9fiR6n89Ilc)
