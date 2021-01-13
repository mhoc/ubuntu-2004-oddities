## System

- Custom-built Desktop
- Ryzen 7 2700
- 32gb DDR4 memory
- 1TB Samsung NVME SSD
- Zotac GTX 1070
- Ubuntu 20.04.1 (ISO downloaded and installed 2021-01-12)
- Primary monitor: Viotek 34" 3440x1440 ultrawide @ 100hz (displayport)
- Secondary monitor: Asus 27" 1440x2560 @ 165hz (configured rotate-right) (displayport)

## Installation

- Installation consistently reports failure when selecting "Install third party drivers" during setup. However, rebooting and removing the flash drive results in a functional installation. This is a known issue, and has existed at least since release.

## Graphics

- System was installed with `xserver-xorg-video-nouveau` drivers by default. Attempting to install `nvidia-driver-460` (latest at time) results in an incomprehensible error message. Installing `nvidia-driver-450` was successful, then upgrading to `nvidia-driver-460` was successful.

- Built-in Ubuntu display configuration is wholly disfunctional, causing the display space of both monitors to partially overlap instead of extend. Very trippy, like half-mirror, half-extend, kind of cool. The nvidia driver control panel functions correctly.

- Lock screen immediately turns monitors off, despite all power save options being disabled in settings.

- Some level of power save sleep causes second monitor to never receive an image, including power-cycling the monitor. Hard reboot is only fix I've found.

- Second monitor is configured in a vertical rotate-right state. Upon every reboot, x-server defaults to rotate-left instead of rotate-right.

## Audio

- System does not appear to have a concept of "preferred" audio devices, and when a device goes missing it always defaults back to a present device, even when the previously "preferred" device reappears. This causes heartache for devices like wireless headphones, which are frequently turned on and off to preserve battery (though, I was happy to see the Logitech G Pro X headphones otherwise function without issue with no additional configuration, including the volume wheel, which never worked properly on Windows despite all necessary drivers being installed).

## Snap

- Any application installed via Snap, such as Slack, will create a second Firefox profile when clicking hyperlinks. Known issue. Permanently fixable by deleting the extra profile in Firefox's `about:profiles`.

- First startup of any Snap application on clean boot can take 10 to 15 seconds. Subsequent startups tend to be faster.

- `aws-cli` (verified package by `Amazon Web Services`): `latest/stable` has not been updated in 2.5 years. [No longer officially maintained by AWS](https://github.com/aws/aws-cli/issues/5142#issuecomment-698565229). Some [evidence](https://github.com/aws/aws-cli/issues/3065#issuecomment-354831511) around their github that current employees on the project don't know who maintains it, or rather, no longer maintains it. Why does Snapcraft still have that package marked as "verified by Amazon Web Services"? There's no evidece Amazon ever maintained it; did Snapcraft give a Verified badge to an individual pretending to be AWS? Very concerning security issue.

- `go:1.15.6` (unverified package, classic confinement): visual studio code (verified snap, classic confinement) go language extensions unable to locate Go binary, with error `cached Go version ({"binaryPath":"/snap/bin/go","version":""}) is invalid, recomputing | unable to determine version from the output of "/snap/bin/go version": "undefined"`. 

- `node:12.19.0` (verified package by `iojs`, classic confinement) (latest in `12/stable` channel on 2021-01-13 despite a high severity CVE in `12.20.0` discovered last week): running `mocha` on an internal, relatively typical nodejs application causes many tests to fail due to 2 second timeout. No issue on any other platform, or in non-Snap nodejs.

## Non-Snap-Related App Issues

- Andorid Studio (both Snap and .tar.gz from Google): fails to start Android virtual machines, with the error "process was killed".

- Firefox: refuses to play most web videos, despite all closed-source third-party super-duper-install options being selected on system install (e.g. Twitch, YouTube). Installing the `libavcodec-extra` via `apt` resolves this.

- Steam (installed via .deb from https://steampowered.com/): refused to launch after initial install. Hard reboot fixes.

- Videos: Cannot play some `.mkv` files which VLC is fully capable of playing; window appears for a split second before disappearing.

