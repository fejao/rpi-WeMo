# WeMo Emulation Server for setting LED's with Amazon Alexa over a Raspberry Pi

## Install the alexa-raspberry (WeMo Emulation Server for Alexa)

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

## Clone this repository
```
$ git clone https://github.com/fejao/rpi-WeMo.git
```

## Set your LED's
Here are the schematics that I used to set my one.

The GPIO's that I'm using is:

**17** Yellow LED

**18** Blue LED

**22** Red LED

**23** Green LED

![Alt text](pics/WeMo_01_bb.png?raw=true "Raspberry Connections")


## Start the Server
```
$ cd alexa-raspberry
```
