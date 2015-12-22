# ffscreencast

[Features](https://github.com/cytopia/ffscreencast#1-features) |
[Usage](https://github.com/cytopia/ffscreencast#2-usage) |
[Screenshots](https://github.com/cytopia/ffscreencast#3-screenshots) |
[Todo](https://github.com/cytopia/ffscreencast#4-todo) |
[Contribution](https://github.com/cytopia/ffscreencast#5-contribution) |
[License](https://github.com/cytopia/ffscreencast#6-license) |
[Version](https://github.com/cytopia/ffscreencast#7-version) |
[Awesome](https://github.com/cytopia/ffscreencast#8-awesome)

[![Build Status](https://travis-ci.org/cytopia/ffscreencast.svg?branch=master)](https://travis-ci.org/cytopia/ffscreencast)
[![Latest Stable Version](https://poser.pugx.org/cytopia/ffscreencast/v/stable)](https://packagist.org/packages/cytopia/ffscreencast) [![Total Downloads](https://poser.pugx.org/cytopia/ffscreencast/downloads)](https://packagist.org/packages/cytopia/ffscreencast) [![Latest Unstable Version](https://poser.pugx.org/cytopia/ffscreencast/v/unstable)](https://packagist.org/packages/cytopia/ffscreencast) [![License](https://poser.pugx.org/cytopia/ffscreencast/license)](http://opensource.org/licenses/MIT)
[![Type](https://img.shields.io/badge/type-bash-red.svg)](https://www.gnu.org/software/bash/)

**About**

`ffscreencast` is a shell wrapper for `ffmpeg` that allows fool-proof screen recording via the command line. It will auto-detect all available monitors, cameras and microphones and is able to interactively or manually choose the desired recording device(s). Additionally `ffscreencast` will let you overlay the camera stream on top of the desktop session.

Besides that `ffscreencast` can act as an ffmpeg command generator. Every available option can also just show the corresponding ffmpeg command instead of executing it. Non-ffmpeg commands, such as how the camera resolution is pulled and others can also be shown instead of being executed.

![Screencast](https://raw.githubusercontent.com/cytopia/ffscreencast/master/doc/img/ffscreencast.png)

**Supported platforms**

| OSX    | Linux | FreeBSD | Windows |
| :----: | :----: | :----: | :----: |
| [![OSX](https://raw.githubusercontent.com/cytopia/icons/master/64x64/osx.png)](https://www.apple.com/osx) | ![Linux](https://raw.githubusercontent.com/cytopia/icons/master/64x64/linux.png) | [![FreeBSD](https://raw.githubusercontent.com/cytopia/icons/master/64x64/freebsd.png)](https://www.freebsd.org) | [![Windows](https://raw.githubusercontent.com/cytopia/icons/master/64x64/windows.png)](https://www.microsoft.com/en-us/windows) |
| via [AVFoundation](https://ffmpeg.org/ffmpeg-devices.html#avfoundation) | via [x11grab](https://ffmpeg.org/ffmpeg-devices.html#x11grab) | coming soon | coming soon |

**Requirements**

| Program  | Required | Description |
| ------------- | ------------- | -------- |
| [bash](https://www.gnu.org/software/bash/)  | yes  | The whole script is written in bash and might not be 100% Posix compliant |
| [ffmpeg](https://www.ffmpeg.org/)  | yes  | The ffmpeg binary must be present |
| [v4l2-ctl](http://linuxtv.org/wiki/index.php/V4l-utils) | Linux | Required for linux to list camera devices |
| [arecord](http://linux.die.net/man/1/arecord) | Linux | Required for linux to list sound devices |
| [xdpyinfo](http://www.x.org/archive/X11R7.6/doc/man/man1/xdpyinfo.1.xhtml) | Linux | Required for linux to list screends |

## 1. Features

* Config file for default configuration
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

Usage: ffscreencast [-s[num]] [--sargs=] [-a[num]] [--aargs=] [-c[num] [--cargs=] [--oargs=] [-e<ext>] [--dry]
       ffscreencast --slist [--dry]
       ffscreencast --alist [--dry]
       ffscreencast --clist [--dry]
       ffscreencast --help
       ffscreencast --version
       ffscreencast --test

When invoked without any arguments, it will start screen recording
on the default screen without sound and without camera overlay.

Input options:
-s[num]           (Default) Enable screen capturing [with device number X].
                  If no device number is specified it will use the default, if only
                  one device is present, otherwise it will ask you to choose one
                  Use: -s or -s1

--sargs=          Additional screen arguments.
                  Specify additional ffmpeg arguments for the screen input device.
                  Use: --sargs="-framerate 30"
                  Default: ''

-a[num]           Enable audio capturing [with device number X]
                  If no device number is specified it will use the default, if only
                  one device is present, otherwise it will ask you to choose one
                  Use: -a or -a1

--aargs=          Additional audio arguments.
                  Specify additional ffmpeg arguments for the audio input device.
                  Use: --aargs="-ac 1"
                  Default: '-ac 2'

-c[num]           Add camera overlay [with device number X]
                  If no device number is specified it will use the default, if only
                  one device is present, otherwise it will ask you to choose one
                  Use: -c or -c1

--cargs=          Additional camera arguments
                  Specify additional ffmpeg arguments for the camera input device.
                  Use: --cargs="-video_size 1280x720"
                  Default: ''


Output options:
-e<ext>           Output video format extension (Default: mkv)
                  E.g.: -emkv, or -eavi, or -emp4

-oargs=           Additional output arguments
                  Specify additional ffmpeg arguments for the output encoding.
                  Use: --oargs="-crf 0"
                  Default: '-crf 0 -preset ultrafast'


Behavior options:
--dry             Show the command (without executing)


List options:
--list            List all devices
--slist           Only list screen capturing devices (monitors)
--alist           Only list audio capturing devices (microphones)
--clist           Only list camera capturing devices (cams)


System information:
--help            Show this help screen
--version         Show version information
--test            Test requirements

```

The `num` (device numbers) can be omitted. If there is only one device of its type available, `ffscreencast` will automatically default to this device, otherwise it will ask interactively which device to use for recording.

### 2.2 Examples

Do a screencast on the default screen (without explicitly choosing the monitor)

```shell
$ ffscreencast
```

List monitors and record on monitor 2 (`Capture screen 0`)

```shell
$ ffscreencast --slist
Available screen recording devices (monitors):

[2] Capture screen 0    Color LCD: Resolution: 2880 x 1800 Retina
[3] Capture screen 1    S2431W: Resolution: 1920 x 1200
[4] Capture screen 2    Thunderbolt Display: Resolution: 2560 x 1440


$ ffscreencast -s2
```

List cameras

```shell
$ ffscreencast --clist
Available camera recording devices:

[0] FaceTime HD Camera (Display) (160x120@29.97 160x120@25 160x120@23.999981 160x120@14.999993 176x144@29.97 176x144@25 176x144@23.999981 176x144@14.999993 320x240@29.97 320x240@25 320x240@23.999981 320x240@14.999993 352x288@29.97 352x288@25 352x288@23.999981 352x288@14.999993 640x480@29.97 640x480@25 640x480@23.999981 640x480@14.999993 960x540@29.97 960x540@25 960x540@23.999981 960x540@14.999993 1024x576@29.97 1024x576@25 1024x576@23.999981 1024x576@14.999993 1280x720@29.97 1280x720@25 1280x720@23.999981 1280x720@14.999993)

[1] FaceTime HD Camera (1280x720@30 640x480@30 320x240@30)

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

ffmpeg -hide_banner -loglevel info -f avfoundation   -i "1" -f avfoundation  -i "0" -c:v libx264 -crf 0 -preset ultrafast -filter_complex 'overlay=main_w-overlay_w-10:main_h-overlay_h-10' "/Users/cytopia/Desktop/Screencast 2015-10-06 at 21.28.01.mkv"

```

## 3. Screenshots

Showing screen recording with and without camera overlay.

![Screencast](https://raw.githubusercontent.com/cytopia/ffscreencast/master/doc/img/ffscreencast.png)
![Screencast](https://raw.githubusercontent.com/cytopia/ffscreencast/master/doc/img/ffscreencast2.png)

## 4. Todo

### 4.1 Bugs

* [ ] **General:** Sound is still behind one second when using camera overlay
* [X] **OSX:** ~~USB Monitors (see [#1](https://github.com/cytopia/ffscreencast/issues/1))~~

### 4.2 Enhancements

* [ ] **BSD:** Support for [Free]BSD (needs testing)
* [ ] **Windows:** Support for Windows (via cygwin and dshow)
* [ ] **Linux:** set sound options via cmd (alsa vs pulse)
* [ ] **Linux:** Get default resolution/framerate for camera
* [X] **OSX:** Get default resolution/framerate for camera
* [X] **General:** ~~Set camera resolution via cmd~~ use `--cargs`
* [ ] **General:** Set camera position via cmd
* [ ] **General:** Be able to record one or multiple screens (monitors)

## 5. Contribution

Contributors are welcome.

## 6. License

[![license](https://poser.pugx.org/cytopia/ffscreencast/license)](http://opensource.org/licenses/mit)

## 7. Version

For a complete list of verion see [CHANGELOG](CHANGELOG.md)

## 8. Awesome

Added by the following [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome) lists:

* [awesome-cli](https://github.com/aharris88/awesome-cli)

