# Pi-handheld
https://www.youtube.com/watch?v=U5T-G7XxYqI
## Software preparation:
### Switch console dependence:
1:
```
sudo apt-get update && sudo apt-get upgrade
sudo apt install cmake
sudo apt install libudev-dev
sudo apt install libevdev-dev
sudo apt install dkms
sudo apt-get install raspberrypi-kernel-headers
git clone https://github.com/nicman23/dkms-hid-nintendo
cd dkms-hid-nintendo
sudo dkms add .
sudo dkms build nintendo -v 3.x   (change 3.x to your version)
sudo dkms install nintendo -v 3.x
```

2:
```
git clone https://github.com/DanielOgorchock/joycond
cd joycond
cmake .
sudo make install
sudo systemctl enable --now joycond
```

3:
```
sudo pip3 install git+https://github.com/joaorb64/joycond-cemuhook
#From now on, you'll only need to run joycond-cemuhook from a terminal.
```

### ROS env installation:
1:
docker: https://phoenixnap.com/kb/docker-on-raspberry-pi

2:
```
sudo docker run --name ros-noetic-env --net host -e DISPLAY=:0 --privileged -it arm64v8/ros:noetic
```
3: GUI
```
#In the terminal (not in docker container)
# Run GUI application in container after following command 
xhost + 
```


## Related projects
- [dkms-hid-nintendo](https://github.com/nicman23/dkms-hid-nintendo): A Nintendo HID kernel module.
- [joycond](https://github.com/DanielOgorchock/joycond): A userspace daemon to
  combine joy-cons from the hid-nintendo kernel driver
- [joycond-cemuhook](https://github.com/joaorb64/joycond-cemuhook): Support for
  cemuhook's UDP protocol for joycond devices
