# Introduction
Button that will use a Raspberry Pi to turn on Philips Hue Lights

## Set Up

I am using a Raspberry Pi 2, but you should be able to use almost any version of the Raspberry Pi without issue.

Make sure you have node.js and npm installed first, as these scripts require it. Also make sure you have python, but most Pi's come with it installed.

What I did was create a Projects folder under home pi: `cd /home/pi` then `mkdir Projects/` and `cd Projects/`

Clone the repo by using: `git clone https://github.com/cwalk/Hue-Button`

Feel free to get rid of the images, circuit diagrams, and README, as all the code is in the `HueButton/` folder and the launcher.sh script.

Make sure you do `npm install` in the `HueButton/` directory. You should now have cylon, cylon-raspi, and cylon-hue installed in node_modules.

If you want more help, check out: https://cylonjs.com, http://cylonjs.com/documentation/platforms/raspberry-pi/, and http://cylonjs.com/documentation/platforms/hue/

## Cron job

What I did was setup a cron job to run my `launcher.sh` script everytime my Pi reboots. This makes it easy because all I have to do is add power to the Pi, and the button starts working after the Pi boots. Now I made `launcher.sh` run on reboot, but all this shell script does is naviagte to my project directory, and run `python button.py`. Please feel free to just set up a cron job to run `python button.py` instead, thats what I would do now (but I was learning while doing this, so lessons learned).

For more help, check out: https://www.raspberrypi.org/documentation/linux/usage/cron.md

## How the Code works

Basically the `button.py` file is always running, thanks to the cron job. This listens for a button press on pin 12. If the button is pressed, we check the lightState flag. If the lights are off, we turn them on. If the lights are on, we turn them off when the button is pressed.

`turnAllOff.js` turns all the lights off, and `turnAllOn.js` turns them all on. This uses nodejs/cylonjs. You will need to substitute your own Philips Bridge information for the HOSTNAME and USERNAME at the tops of both of these files.

## Circuit

Here is the circuit diagram I made. I have 3.3V connected to a 1K Ohm resistor, which is wired to the pushbutton, and the singal pin (pin 12). The other leg of the pushbutton is connected to GND.

![HueButton](/HueButton.png?raw=true "HueButton")

## YouTube

YouTube: 

## Pictures

![Breadboard](/Breadboard.jpg?raw=true "Breadboard")
