# backlight.sh

Linux backlight control in ~100 lines ([SLOC](https://dwheeler.com/sloccount))
of POSIX compliant shell.

# Features

* Set the backlight value (duh)
* Increase or decrease the backlight value, relatively
* Set or adjust backlight by percentage
* Gradually fade to the desired backlight value (optional)

# Examples

`usage: backlight [-hsV] [-d device] -- [+|-]<num>[%]`

```shell
# set the backlight to 50%
# first device found in /sys/class/backlight
backlight 50%
# increase the backlight amdgpu_bl0 by 25%
backlight -d amdgpu_bl0 +25%
# decrease the backlight acpi_video0 by 40, smoothly
# '--' may be omitted when increasing or setting the backlight...
# ...but is required when decreasing
backlight -d acpi_video0 -s -- -40
```

# Motivation

## Why?

I wanted a simple backlight control utility and I wanted to constrain myself
to be POSIX compliant. `backlight` only targets Linux, and Linux often has bash
(nearly always in a desktop context); therefore the POSIX compliance is more of
a gimmick. But hey, it works with `ash`, `dash`, `yash`...

## What about [`brightnessctl`](https://github.com/Hummer12007/brightnessctl), [`lux`](https://github.com/Ventto/lux), [`backlight_control`](https://github.com/Hendrikto/backlight_control)...

Realistically, any one of these utilities will work fine to adjust your
backlight. Some of them have disjoint features. My reasons for writing my own
are as follows:

* I felt like writing something.
* I wanted to make is POSIX compliant.
* `lux`: Makes frequent calls to external utilities and uses the poorly-defined
  `echo`. Realistically, this doesn't matter.
* `backlight_control`: Dead-simple, which is great! Lacks some features of
  `backlight` (as designed).

Overall, I really just felt like writing this and had opinions about how it
should be designed.

`backlight` is not designed to replace any of these utilities. I built it for my
own enjoyment, but you should use whichever one has the features you care about!
I particularly enjoy the optional `logind` integration of `brightnessctl`.

# Contributing

Pull requests are always welcome.

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
licensed under the terms of the ISC License.

## Style

`backlight` strives to be POSIX compliant. [`shellcheck`](https://www.shellcheck.net)
best practices should be obeyed wherever possible.

# Versioning

This project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Changes are documented in the [Changelog](CHANGELOG.md).

See the [tags](https://github.com/owenthewizard/backlight/tags) for available releases.

# Authors

See [the list of contributors](https://github.com/owenthewizard/backlight/contributors).

# License

`backlight` is licensed under the [ISC License](LICENSE.md). Feel free to use,
share, and hack!


