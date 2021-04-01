# Raspberry-pi-automatic-active-cooling
An automatic fan speed control for RPI4 depending upon the temprature using python script.


## Hardware
Simple hardware using FET to control fan switching.

![alt text](https://github.com/ash-win-cs/raspberry-pi-automatic-active-cooling/blob/main/assets/hardware.jpg "Hardware")

R1 to discharge the gate capacitance of the MOSFET, and R2 to limit the current which is created if you change the signal at the gate. R1 is usually a few k Ohms, and R2 a few 100 ohms.

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

* Now copy `fancontroll.py` & `launcher.sh` from PC to RPI `Scripts` folder, this can be done using many methods here I will use `SCP` command for sending files over SSH
```
scp fancontroll.py root@192.168.43.112:Scripts/

scp launcher.sh root@192.168.43.112:Scripts/
```
> note that ssh client should be installed on both sides (PC & RPI) use the below code to install.
```apt-get install openssh-client```


* Now run the python code using the command
```python fancontroll.py```


* Now we add a directory to store the error log files
```
cd 
mkdir logs
```

* Now to automatically start the python script on rpi reboot use the following commands
The below code makes `launcher.sh` files executable
```
cd
cd Scripts/
bash launcher.sh
sh ./launcher.sh
```
```
chmod 755 launcher.sh
```

Now open crontab to add `launcher.sh` path to automaticaly start after reboot
```
sudo crontab -e 
```

At the end of the file add the following line and save the file
```
@reboot sh /root/Scripts/launcher.sh >/root/logs/cronlog 2>&1
```
* Now reboot the RPI to get the changes saved

References : 
* [Andreas Spiess 1](https://www.sensorsiot.org/pimp-my-raspberry-pi-3/)
* [Andreas Spiess 2](https://www.sensorsiot.org/variable-speed-cooling-fan-for-raspberry-pi-using-pwm-video138/)
* [SCP File Transfer RPI Documentation](https://www.raspberrypi.org/documentation/remote-access/ssh/scp.md)