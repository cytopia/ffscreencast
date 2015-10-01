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

ffscreencast is a shell wrapper for ffmpeg that allows easy screen recording including camera overlay. It works with multiple monitors and camera devices.

[![OSX](https://raw.githubusercontent.com/cytopia/ffscreencast/master/img/ffscreencast.png)](https://www.apple.com/osx)


##### Tested on
[![OSX](https://raw.githubusercontent.com/cytopia/icons/master/64x64/osx.png)](https://www.apple.com/osx)



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

To simply start desktop recording your screen call the program without any arguments `ffscreencast` and it will use the default screen without camera overlay and without sound.

```shell
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
```

## 3. Screenshots



## 4. Todo

* Sound is still not working properly
* Support for Linux and BSD


## 5. Contribution
Contributors are welcome.


## 6. License
[![license](https://poser.pugx.org/cytopia/ffscreencast/license)](http://opensource.org/licenses/mit)


## 7. Version
For a complete list of verion see [CHANGELOG](CHANGELOG.md)
