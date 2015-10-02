# ffscreencast

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


![Screencast](https://raw.githubusercontent.com/cytopia/ffscreencast/master/img/ffscreencast.png)


##### Tested on
[![OSX](https://raw.githubusercontent.com/cytopia/icons/master/64x64/osx.png)](https://www.apple.com/osx) via [AVFoundation](https://ffmpeg.org/ffmpeg-devices.html#avfoundation)



##### Requirements
| Program  | Required | Description |
| ------------- | ------------- | -------- |
| [bash](https://www.gnu.org/software/bash/)  | yes  | The whole script is written in bash and might not be 100% Posix compliant |
| [ffmpeg](https://www.ffmpeg.org/)  | yes  | The ffmpeg binary must be present |


## 1. Features

* Screen recording
* Camera overlay
* Audio support
* Allows to manually (parameter) or interactively choose monitor
* Allows to manually (parameter) or interactively choose camera
* Allows to manually (parameter) or interactively choose sound device

## 2. Usage

### 2.1 Overview

To simply start desktop recording your screen call the program without any arguments `ffscreencast` and it will use the default screen without camera overlay and without sound.

```shell
$ ffscreencast

Usage: ffscreencast [-s[num]] [-a[num]] [-c[num]]
       ffscreencast --slist
       ffscreencast --alist
       ffscreencast --clist

When invoked without any arguments, it will start
screen recording on the default screen without sound
and without camera overlay.

Recording options (can be combined):
-s[num]       (Default) Enable screen capturing [with device number X]
-a[num]       Enable audio capturing [with device number X]
-c[num]       Add camera overlay [with device number X]

Display options:
--slist       List screen capturing devices
--alist       List audio capturing devices
--clist       List camera capturing devices
--help        Show this help screen
--version     Show version information
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
