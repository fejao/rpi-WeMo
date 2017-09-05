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

### gpio-set.py Script
The script can have such input:
```
$ ./gpio-set.py [-h] [-v] [-s SET_LED] [-g GPIO_NUM] [-c COLOR_NAME]
```

With optional arguments:

*  **-h, --help**
  * show help message and exit
*  **-v, --verbose**
  * increase output verbosity
*  **-s SET, --set SET**
  * Set the GPIO ('on', 'off'), default: off
*  **-g GPIO_NUM, --gpio-num GPIO_NUM**
  * Number for the GPIO input, default: 18
*  **-c COLOR_NAME, --color-name COLOR_NAME**
  * Color name: 'blue', 'green', 'red' and 'yellow'

The default *GPIO* is set to be use the **18**, you can change this at the script over the *global variable* **DEFAULT_GPIO**

```
DEFAULT_GPIO = <YOUR_DEFAULT_GPIO>
```

For example to turn **on** the **17** GPIO you should run:
```
$ ./gpio-set.py -s on -g 17
```

And to turn **off** the **23** GPIO you should run:
```
$ ./gpio-set.py -s off -g 23
```

### wemo-devices.json File

Feel free to use different *GPIO's*, just don't forget to update the **devices.json** file and change from:
You can change the file to use your own command:

```
{
  "<YOUR_COMMAND_NAME_HERE>":{
    "oncommand": "./gpio-set.py -s on -g <YOUR_GPIO_NUMBER> -v"
    "offcommand": "./gpio-set.py -s off -g <YOUR_GPIO_NUMBER> -v"
  }
}
```

For example, to use the command as **Test LED** using the **22** GPIO you should use as:
```
{
  "Test LED":{
    "oncommand": "./gpio-set.py -s on -g 22 -v"
    "offcommand": "./gpio-set.py -s off -g 22 -v"
  }
}
```

_____________________________________________
## 4 - Start the Server
```
$ cd rpi-WeMo
$ alexa-raspberry wemo-devices.json
```

### Add to startup
You could also add it to the startup of the system creating a *systemd* file.

```
$ sudo nano /lib/systemd/system/alexawemo.service
```

Add to the **alexawemo.service** file:

```
[Unit]
Description=Alexa Wemo emulation server for RaspberryPi
After=network.target

[Service]
#WorkingDirectory=<LOCATION_OF_wemo-devices.json_AND_gpio-set.py_FILE>
WorkingDirectory=/home/pi/rpi-WeMo
ExecStart=/usr/local/bin/alexa-raspberry wemo-devices.json
Restart=always
RestartSec=10
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=Alexa-Raspberry

[Install]
WantedBy=multi-user.target system start
WantedBy = multi-user.target
```

### Enable the service
In order to use every single restart, it is needed to enable the service
```
$ sudo systemctl enable alexawemo.service
```

### Start the service
```
$ sudo systemctl start alexawemo.service
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
