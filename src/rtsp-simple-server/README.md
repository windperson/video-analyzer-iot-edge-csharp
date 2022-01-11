# Use RTSP simple server and WebCam as video analyzer source 

Get the [rtsp-simple-server](https://github.com/aler9/rtsp-simple-server) of the platform that USB WebCam is connected to.

Then use the config file `rtsp-simple-server.yml` inside this folder to configure the RTSP server.

## Install video4linux troubleshooting tools on Ubuntu ##

```
sudo apt install v4l-utils mplayer -y
```

v4l2-ctl command list:
https://www.mankier.com/1/v4l2-ctl

* Get sw & hw details of the "/dev/video0" video device:
   ```
   v4l2-ctl --all --device /dev/video0
   ```

* Get supported video formats and resolutions of the "/dev/video0" video device:
   ```
   v4l2-ctl --list-formats-ext --device /dev/video0
   ```

* Open a video preview window using 800x600 resolution on "/dev/video0" video device:
   ```
   mplayer tv:// -tv driver=v4l2:width=800:height=600:device=/dev/video0
   ```

* Watch the real RTSP video stream:
   ```
   mplayer rtsp://[ip address]:8554/cam
   ```