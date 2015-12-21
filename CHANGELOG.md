Version 0.6 (unreleased)
-----------

- [Enh] Major code rewrite to better support new methods/os
- [Fix] Only check for requirements that are being requested (e.g. Only check for cam if you want a cam overlay.)

Version 0.5
-----------

- [Fix] Fixed quoting issue
- [Enh] Pass shellcheck
- [Fix] Remove `-video_size` option if no resolution was found
- [Fix] Replaced commands (grep, awk, sed) with full system path to avoid aliases


Version 0.4 (beta)
-----------

- [Fix] OSX: Get default camera resolution/framerate for recording
- [Enh] Code comments
- [Enh] OSX: List camera resolutions and framerates
- [Fix] Audio delay (without camera overlay)
- [Fix] Fixed broken sound (now only delays about 1 second with cam overlay)


Version 0.3 (beta)
-----------

- [Enh] Code cleanup
- [Enh] OSX: Better screen (monitor) information
- [Enh] Being able to change custom ffmpeg options via cmd argument


Version 0.2 (beta)
-----------

- Added basic linux support
- Added version information
- Added check requirements
- [Enh] Be able to list the ffmpeg command only
- [Enh] Performance improvements on wrong commands


Version 0.1 (alpha)
-----------

- screencast with video overlay

