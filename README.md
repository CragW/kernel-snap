# Build yourself a Ubuntu kernel snap
Sample snapcraft.yaml for advanced users who want to rebuild the kernel from Ubuntu official kernel source.


## Introduction
Supported Hardware:
```
1. Dell Edge Gateway 3001/3002/3003
2. Dell Edge Gateway 5000/5100
```

Target OS:
```
Ubuntu Core 16
```

Build Environment:
```
Ubuntu Desktop 16.04 64bit
```


## Building a Custom Kernel - HowTo
Kernel source code
```
$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-xenial.git
```
Preparation
```
$ sudo apt-get update
$ sudo apt-get build-dep linux-image-$(uname -r)
```
Download sample files
```
$ git clone https://github.com/CragW/kernel-snap.git
$ cd kernel-snap
```
Build the kernel snap
```
$ sudo snapcraft
```

The time to finish the build depends on the configuration of build machine. 
At the end, *kernel-x_4.x_amd64.snap* will be generated in the same directory.

## Notes
* Testing a custom built kernel snap requires switching off *Secure Boot* in the BIOS.
* No support/maintainence for custom built kernel snap.

## Testing
On the supported hardware devices, check the current kerne1 snap revision:
```
$ snap list
```
For example: (The revision is *40*)
```
Name                Version        Rev  Developer  Notes
caracalla-kernel    4.4.0-2002.2   40   canonical  -
```
Backup the r40 kernel snap
```
$ cp /var/lib/snapd/snaps/caracalla-kernel_40.snap ~/
```
Replace the current kernel snap with developing(custom built) kernel snap
```
$ sudo cp <name of devel kernel snap> /var/lib/snapd/snaps/caracalla-kernel_40.snap
```
Reboot the system and test the kernel
```
$ sudo reboot
```

## Restore kernel snap
Copy back the original kernel snap
```
$ sudo cp ~/caracalla-kernel_40.snap /var/lib/snapd/snaps/caracalla-kernel_40.snap
```
Reboot the system
```
$ sudo reboot
```

## OS Recovery
When things go wrong, you may factory restore the system entirely.







