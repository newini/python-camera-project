https://raspberrypi-guide.github.io/electronics/using-usb-webcams

## 0. Prepare
### 0.1 enable x server
on server side
```
sudo apt install xauth
sudo reboot
```

- test
```
sudo apt install x11-apps
xeyes
```


### 0.2 check usb camera works
- check if usb camera is connected
```
lsusb
```
e.g. result
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1bcf:28c4 Sunplus Innovation Technology Inc. FHD Camera Microphone
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

- find usb camera number

- test
```
sudo apt install fswebcam
sudo usermod -a -G video youruser
sudo reboot
fswebcam -d /dev/video1 -r 1280x720 --no-banner image.jpg
```


## open
sudo apt-get install shotwell
shotwell image.jpg



## video
sudo apt install ffmpeg
ffmpeg -f v4l2 -video_size 1280x720 -i /dev/video0 -frames 1 out.jpg
