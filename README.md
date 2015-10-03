# ffscreencast (beta)

[Features](https://github.com/cytopia/ffscreencast#1-features) |
[Usage](https://github.com/cytopia/ffscreencast#2-usage) |
[Screenshots](https://github.com/cytopia/ffscreencast#3-screenshots) |
[Todo](https://github.com/cytopia/ffscreencast#4-todo) |
[Contribution](https://github.com/cytopia/ffscreencast#5-contribution) |
[License](https://github.com/cytopia/ffscreencast#6-license) |
[Version](https://github.com/cytopia/ffscreencast#7-version)

[![Build Status](https://travis-ci.org/cytopia/ffscreencast.svg?branch=master)](https://travis-ci.org/cytopia/ffscreencast)
[![Latest Stable Version](https://poser.pugx.org/cytopia/ffscreencast/v/stable)](https://packagist.org/packages/cytopia/ffscreencast) [![Total Downloads](https://poser.pugx.org/cytopia/ffscreencast/downloads)](https://packagist.org/packages/cytopia/ffscreencast) [![Latest Unstable Version](https://poser.pugx.org/cytopia/ffscreencast/v/unstable)](https://packagist.org/packages/cytopia/ffscreencast) [![License](https://poser.pugx.org/cytopia/ffscreencast/license)](http://opensource.org/licenses/MIT)
[![Type](https://img.shields.io/badge/type-bash-red.svg)](https://www.gnu.org/software/bash/)


##### About
`ffscreencast` is a shell wrapper for `ffmpeg` that allows fool-proof screen recording via the command line. It will auto-detect all available monitors, cameras and microphones and is able to interactively or manually choose the desired recording device(s). Additionally `ffscreencast` will let you overlay the camera stream on top of the desktop session.

Besides that `ffscreencast` can act as an ffmpeg command generator. Every available option can also just show the corresponding ffmpeg command instead of executing it.


![Screencast](https://raw.githubusercontent.com/cytopia/ffscreencast/master/img/ffscreencast.png)


##### Tested on
| OSX    | Debian | CentOS |
| :----: | :----: | :----: |
| [![OSX](https://raw.githubusercontent.com/cytopia/icons/master/64x64/osx.png)](https://www.apple.com/osx) | [![Debian](https://raw.githubusercontent.com/cytopia/icons/master/64x64/debian.png)](https://www.debian.org) | [![CentOS](https://raw.githubusercontent.com/cytopia/icons/master/64x64/centos.png)](https://www.centos.org) |
| via [AVFoundation](https://ffmpeg.org/ffmpeg-devices.html#avfoundation) | via [x11grab](https://ffmpeg.org/ffmpeg-devices.html#x11grab) | via [x11grab](https://ffmpeg.org/ffmpeg-devices.html#x11grab) |



##### Requirements
| Program  | Required | Description |
| ------------- | ------------- | -------- |
| [bash](https://www.gnu.org/software/bash/)  | yes  | The whole script is written in bash and might not be 100% Posix compliant |
| [ffmpeg](https://www.ffmpeg.org/)  | yes  | The ffmpeg binary must be present |
| [v4l2-ctl](http://linuxtv.org/wiki/index.php/V4l-utils) | Linux | Required for linux to list camera devices |
| [arecord](http://linux.die.net/man/1/arecord) | Linux | Required for linux to list sound devices |
| [xdpyinfo](http://www.x.org/archive/X11R7.6/doc/man/man1/xdpyinfo.1.xhtml) | Linux | Required for linux to list screends |


## 1. Features

* Screen recording
* Camera overlay
* Audio support
* Allows to manually (parameter) or interactively choose monitor
* Allows to manually (parameter) or interactively choose camera
* Allows to manually (parameter) or interactively choose sound device
* ffmpeg command generation

## 2. Usage

### 2.1 Overview

To simply start desktop recording your screen call the program without any arguments `ffscreencast` and it will use the default screen without camera overlay and without sound.

```shell
$ ffscreencast

Usage: ffscreencast [-s[num]] [-a[num]] [-c[num]] [--dry]
       ffscreencast --slist [--dry]
       ffscreencast --alist [--dry]
       ffscreencast --clist [--dry]

When invoked without any arguments, it will start screen recording
on the default screen without sound and without camera overlay.

Recording options (can be combined):
-s[num]       (Default) Enable screen capturing [with device number X]
-a[num]       Enable audio capturing [with device number X]
-c[num]       Add camera overlay [with device number X]

Behavior options (combine with recording- or list options):
--dry         Show the command (without executing)

List options:
--slist       List screen capturing devices (monitors)
--alist       List audio capturing devices (microphones)
--clist       List camera capturing devices (cams)

System information:
--help        Show this help screen
--version     Show version information
--test        Test requirements
```

The `num` (device numbers) can be omitted. If there is only one device of its type available, `ffscreencast` will automatically default to this device, otherwise it will ask interactively which device to use for recording. 

### 2.2 Examples

Do a screencast on the default screen (without explicitly choosing the monitor)
```shell
$ ffscreencast
```

List monitors and record on monitor 2
```shell
$ ffscreencast --slist
Available screen recording devices:

[1] Capture screen 0
[2] Capture screen 1

$ ffscreencast -s2
```

List cameras
```shell
$ ffscreencast --clist
Available camera recording devices:

[0] FaceTime HD Camera
```

Start a screencast with camera overlay (only one camera present)
```shell
$ ffscreencast -c
```
or select the camera device
```shell
$ ffscreencast -c0
```

Show the ffmpeg command for camera recording
```shell
$ ffscreencast -c --dry

ffmpeg -hide_banner -loglevel info -f avfoundation -framerate 30 -i "1" -f avfoundation -framerate 30 -video_size 1280x720 -i "0" -filter_complex "overlay=main_w-overlay_w-10:main_h-overlay_h-10" "/Users/cytopia/Desktop/Screencast 2015-10-03 at 12.48.00.mkv"

```

## 3. Screenshots

Showing screen recording with and without camera overlay.

![Screencast](https://raw.githubusercontent.com/cytopia/ffscreencast/master/img/ffscreencast.png)
![Screencast](https://raw.githubusercontent.com/cytopia/ffscreencast/master/img/ffscreencast2.png)


## 4. Todo

* Sound is still not working properly
* Support for Linux and BSD


## 5. Contribution
Contributors are welcome.


## 6. License
[![license](https://poser.pugx.org/cytopia/ffscreencast/license)](http://opensource.org/licenses/mit)


## 7. Version
For a complete list of verion see [CHANGELOG](CHANGELOG.md)
