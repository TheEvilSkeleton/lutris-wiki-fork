# Installing Lutris

Table of contents
=============
- [Requirements](#requirements)
 - [Arch / Manjaro / Other Arch derivatives](#arch--manjaro--other-arch-derivatives)
	- [Prerequisites](#prerequisites)
		- [Multilib (Manjaro excluded)](#multilib-manjaro-excluded)
		- [AMD](#amd)
		- [Intel](#intel)
		- [Nvidia](#nvidia)
	- [Installation](#installation)
 - [Fedora](#fedora)
	- [Prerequisites](#prerequisites-1)
		- [Nvidia](#nvidia-1)
	- [Installation](#installation-1)
 - [Gentoo / Funtoo / Other Gentoo derivatives](#gentoo--funtoo--other-gentoo-derivatives)
	- [Prerequisites](#prerequisites-2)
		- [AMD](#amd-1)
		- [Intel](#intel-1)
		- [Nvidia](#nvidia-1)
	- [Installation](#installation-2)
 - [openSUSE](#opensuse)
	- [Prerequisites](#prerequisites-3)
	- [Installation](#installation-3)
 - [Ubuntu / Linux Mint / Other Ubuntu-based distributions](#ubuntu--linux-mint--other-ubuntu-based-distributions)
	- [Prerequisites](#prerequisites-4)
		- [AMD / Intel](#amd--intel-1)
		- [Nvidia](#nvidia-1)
	- [Installation](#Installation-4)
 - [External Sources](#external-sources)

## Requirements

**Before reading through the page, you must ensure that your [GPU is capable of running in Vulkan.](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility)**


## Arch / Manjaro / Other Arch derivatives:

### Prerequisites

#### Multilib (Manjaro excluded)

First, enable multilib.

To enable multilib repository, uncomment the `[multilib]` section in `/etc/pacman.conf`. This process does not require for Manjaro users as it is enabled by default.

```
/etc/pacman.conf
-------------------------------------------------------------------------------------
[multilib]
Include = /etc/pacman.d/mirrorlist
```

Then, upgrade the system by executing the following command as root:

```bash
pacman -Syu
```

#### AMD


To install support for the Vulkan API, execute the following command as root:

```bash
pacman -S lib32-mesa vulkan-radeon lib32-vulkan-radeon vulkan-icd-loader lib32-vulkan-icd-loader
```

#### Intel

To install support for the Vulkan API, execute the following command as root:

```bash
pacman -S lib32-mesa vulkan-intel lib32-vulkan-intel vulkan-icd-loader lib32-vulkan-icd-loader
```

#### Nvidia:

To install support for the Vulkan API, you must install the **proprietary** drivers.

To install them, execute the following command as root:

```bash
pacman -S nvidia nvidia-utils lib32-nvidia-utils nvidia-settings vulkan-icd-loader lib32-vulkan-icd-loader
```
### Installation

To install Lutris, execute the following command as root:

```bash
pacman -S lutris
```

## Fedora

**Note: this is specifically for Fedora 31 on the x86_64 platform. The installation process may be different for different versions of Fedora and platform.**

### Prerequisites

#### AMD / Intel

To install support for the Vulkan API, execute the following command as root:

```bash
dnf install vulkan-tools.x86_64 mesa-vulkan-drivers.x86_64 vulkan-loader.x86_64 vulkan-validation-layers.x86_64
```

#### Nvidia

To install support for the Vulkan API, you must follow these steps:

- enable the [RPM Fusion repository as well as its nonfree repository](https://docs.fedoraproject.org/en-US/quick-docs/setup_rpmfusion/);
- [determine your GPU's model](https://rpmfusion.org/Howto/NVIDIA#Determining_your_card_model);
- [install the drivers for the appropriate model](https://rpmfusion.org/Howto/NVIDIA#Installing_the_drivers).

To install support for the Vulkan API, execute the following command as root:

```bash
dnf install vulkan-tools.x86_64 mesa-vulkan-drivers.x86_64 vulkan-loader.x86_64 vulkan-validation-layers.x86_64
```

**(Optional): during this installation, `DNF` will ask if the GPG fingerprint is correct.  You can check if it is correct in [RPM Fusion's page](https://rpmfusion.org/keys) to make sure that the fingerprint you check matches your version of Fedora.**

### Installation

To install Lutris. execute the following command as root:

```bash
dnf install lutris
```

## Gentoo / Funtoo / Other Gentoo derivatives

### Prerequisites

#### AMD

If you are using an AMD GPU, you will have to read through the [AMD GPU Gentoo wiki](https://wiki.gentoo.org/wiki/Amdgpu) page before proceeding.

Then, to install support for the Vulkan API, execute the following command as root:

```bash
emerge --ask --verbose dev-util/vulkan-tools dev-util/vulkan-headers media-libs/vulkan-layers media-libs/vulkan-loader
```

#### Intel

If you are using an Intel iGPU, you will have to read through the [Intel Gentoo wiki](https://wiki.gentoo.org/wiki/Intel) page before proceeding.

Then, to install support for the Vulkan API, execute the following command as root:

```bash
emerge --ask --verbose dev-util/vulkan-tools dev-util/vulkan-headers media-libs/vulkan-layers media-libs/vulkan-loader
```

#### Nvidia

If you are using an Nvidia GPU, you will have to read through the [Nvidia-drivers Gentoo wiki](https://wiki.gentoo.org/wiki/NVIDIA/nvidia-drivers) page before proceeding.

Then, to install support for the Vulkan API, execute the following command as root:

```bash
emerge --ask --verbose dev-util/vulkan-tools dev-util/vulkan-headers media-libs/vulkan-loader
```

### Installation

To install Lutris, execute the following command as root:

```bash
emerge --ask --verbose games-util/lutris
```

## openSUSE

### Prerequisites

### Installation


## Ubuntu / Linux Mint / Other Ubuntu-based distributions:

### AMD / Intel:

**If you have Ubuntu 19.10 or newer:**
Enable 32 bit architecture (if you haven't already):

```bash
dpkg --add-architecture i386 
```

Install support for 32-bit games:

```bash
apt install libgl1-mesa-dri:i386
```

To install support for the Vulkan API, execute the following command as root:

```bash
apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386
```

Reboot to apply changes.

### Nvidia:

To get the latest Nvidia drivers it is necessary to add the [Proprietary GPU Drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa):

```bash
add-apt-repository ppa:graphics-drivers/ppa
```

Enable 32 bit architecture (if you haven't already):

```bash
dpkg --add-architecture i386 
```

Update to refresh packages:

```bash
apt update
```

Install the 430.40 driver:

```bash
apt install nvidia-driver-430 libnvidia-gl-430 libnvidia-gl-430:i386
```

To install support for the Vulkan API, execute the following command as root:

```bash
apt install libvulkan1 libvulkan1:i386
```

Reboot to apply changes.


**If you have Ubuntu 18.04 Bionic Beaver or Ubuntu 18.10 Cosmic Cuttlefish:**

Add [kisak-mesa PPA](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa): 

```bash
add-apt-repository ppa:kisak/kisak-mesa
```

Enable 32 bit architecture (if you haven't already):

```bash
dpkg --add-architecture i386 
```

Upgrade your system:

```bash
apt update && apt upgrade
```

Install support for 32-bit games:

```bash
apt install libgl1-mesa-glx:i386 libgl1-mesa-dri:i386
```

To install support for the Vulkan API, execute the following command as root:

```bash
apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386
```

Reboot to apply changes.

_Note: Only Ubuntu 18.04 and higher is supported for AMD and Intel graphics._

_Note for Intel integrated graphics users: Only Skylake, Kaby Lake, and Coffee Lake offer full Vulkan support. Broadwell, Haswell and Ivy Bridge only offer partial support, which may not work with a lot of games. Sandy Bridge and older lack any Vulkan support whatsoever._


## External Sources

[Wikipedia / Lutris](https://en.wikipedia.org/wiki/Lutris)

[Gentoo wiki / Lutris](https://wiki.gentoo.org/wiki/Lutris)
