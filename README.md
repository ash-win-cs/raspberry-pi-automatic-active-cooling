# Raspberry-pi-automatic-active-cooling
An automatic fan speed control for RPI4 depending upon the temprature using python script.

References : 
* [Andreas Spiess 1](https://www.sensorsiot.org/pimp-my-raspberry-pi-3/)
* [Andreas Spiess 2](https://www.sensorsiot.org/variable-speed-cooling-fan-for-raspberry-pi-using-pwm-video138/)
* [SCP File Transfer RPI Documentation](https://www.raspberrypi.org/documentation/remote-access/ssh/scp.md)

## Hardware
Simple hardware using FET to control fan switching.

![alt text](https://github.com/ash-win-cs/raspberry-pi-automatic-active-cooling/blob/main/assets/hardware.jpg "Hardware")

## Software setup

* Power up the RPI and open terminal and create a new directory named _scripts_
```
cd
mkdir Scripts
```

* Change directory to Scripts
```
cd Scripts
```

* Now copy the python file from PC to RPI `Scripts` folder, that can be done using many methods here I will use `SCP` command for sending files over SSH
```
scp fancontroll.py root@192.168.43.112:Scripts/
```
> note that ssh client should be installed on both sides (PC & RPI) use the below code to install.
```apt-get install openssh-client```

* Now run the python code using the command
```python fancontroll.py```

* 


