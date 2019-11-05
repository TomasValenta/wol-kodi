# Wake up Kodi using Yatse, Kore or any other Remote!
This script will allow you to start [kodi](http://kodi.tv/about/) on your media center using [yatse](http://yatse.tv/redmine/projects/yatse), [kore](http://kodi.wiki/view/Kore) or [any other](http://kodi.wiki/view/Official_Kodi_Remote/iOS) remote control. Once it is running, the script will be listening to any upcomming WoL message to run the command to start kodi service.

The script has been successfully tested on [Raspbian (Buster)](https://www.raspberrypi.org/downloads/raspbian/) and [archlinux ARM](http://archlinuxarm.org/) although it should work as well on any systemd based operating systems.

## Prerequisites

### Python

This script is written in Python v3. Depending on the operating system you want to run this on, this might be an issue. However, its code is so simple that "it should also work :tm:" with earlier versions of python too.

OK, so as you might guess it already, you will need Python installed on your system to run it.

Python comes installed by default on many distributions, check if it is included on yours with the following command.

```
[root@archberry2 ~]# python --version
Python 3.5.1
```

If this is not your case, install ```python3``` via your system package manager.

### Remote Control

To make it work you will need to configure Kodi to allow to be controlled by other devices. Since you are most likely using Yatse, Kore or other remotes already, it is quite probably that this step has been already done.

Anyway, it doesn't hurt to check the official [Quick set up guide](http://kodi.wiki/view/Smartphone/tablet_remotes) and verify that everything is configured as it should be.

## Script Installation

Get the script and copy it onto /usr/lib/systemd/scripts/wolkodi
```
sudo wget -O /usr/lib/systemd/scripts/wolkodi https://raw.githubusercontent.com/TomasValenta/wol-kodi/python/wolkodi.py
```
Create a new systemd unit so the system can operate and manage the script.
```
sudo wget -O /usr/lib/systemd/system/wolkodi.service https://raw.githubusercontent.com/TomasValenta/wol-kodi/python/wolkodi.service
```

After these modifications, reload the systemd configuration.
```
sudo systemctl daemon-reload
```

## Trying it out

In order to test it, you can run it with the following command:
```
sudo systemctl start wolkodi &
```
You should inmediately start seeing some logs on /var/log/wolkodi.log

If you are happy with the script and you want it to be started automatically on bootup:
```
sudo systemctl enable wolkodi
```

Andddd... you are done :)
