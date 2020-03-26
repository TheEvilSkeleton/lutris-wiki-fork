# Installing Lutris

Table of contents
=============
- [Requirements](#requirements)
 - [Arch / Manjaro / Other Arch derivatives](#arch--manjaro--other-arch-derivatives)
	- [Prerequisites](#prerequisites)
		- [Multilib](#multilib)
		- [AMD](#amd)
		- [Intel](#intel)
		- [Nvidia](#nvidia)
	- [Installation](#installation)
 - [Fedora](#fedora-incomplete-guide)
	- [Prerequisites](#prerequisites-1)
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

## Requirements

**Before reading through the page, you _must_ ensure that your GPU is capable of running in Vulkan.**

## Arch / Manjaro / Other Arch derivatives:

### Prerequisites

#### Multilib

First, enable multilib.

To enable multilib repository, uncomment the `[multilib]` section in `/etc/pacman.conf`

```
/etc/pacman.conf
-------------------------------------------------------------------------------------
[multilib]
Include = /etc/pacman.d/mirrorlist
```

Then, upgrade the system by executing:

```
sudo pacman -Syu
```

#### AMD


To install support for the Vulkan API  (will be functional only if you have a [Vulkan capable GPU](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility)) and 32-bit games, execute:

	sudo pacman -S lib32-mesa vulkan-radeon lib32-vulkan-radeon vulkan-icd-loader lib32-vulkan-icd-loader

#### Intel

To install support for the Vulkan API  (will be functional only if you have a [Vulkan capable GPU](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility)) and 32-bit games, execute:

	sudo pacman -S lib32-mesa vulkan-intel lib32-vulkan-intel vulkan-icd-loader lib32-vulkan-icd-loader

_Note: Only Skylake, Kaby Lake, and Coffee Lake offer full Vulkan support. Broadwell, Haswell and Ivy Bridge only offer partial support, which may not work with a lot of games. Sandy Bridge and older lack any Vulkan support whatsoever._

#### Nvidia:

_**Warning**: Please ensure your graphics card is supported by modern Nvidia driver before installing._
_For a list of supported GPUs click here: https://www.nvidia.com/Download/driverResults.aspx/149138/en-us_

Proprietary driver and support for Vulkan are required for proper functionality of games.

To install it, execute following command:

	sudo pacman -S nvidia nvidia-utils lib32-nvidia-utils nvidia-settings vulkan-icd-loader lib32-vulkan-icd-loader

### Installation

To install Lutris, execute the following command:

	sudo pacman -S lutris

## Fedora (Incomplete Guide)

To install support for the Vulkan API  (will be functional only if you have a [Vulkan capable GPU](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility)) and 32-bit games, execute:

	sudo dnf install vulkan-loader vulkan-loader.i686

### Prerequisites

### Installation
To install Lutris run the following command:
```
sudo dnf install lutris
```
## Gentoo / Funtoo / Other Gentoo derivatives

### Prerequisites

#### AMD

If you are using an AMD GPU, you will have to read through the [AMD GPU Gentoo wiki](https://wiki.gentoo.org/wiki/Amdgpu) page before proceeding.

Then, to install support for the Vulkan API (will be functional only if you have a [Vulkan capable GPU](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility) and driver), execute:

	sudo emerge --ask --verbose dev-util/vulkan-tools dev-util/vulkan-headers media-libs/vulkan-layers media-libs/vulkan-loader

#### Intel

If you are using an Intel iGPU, you will have to read through the [Intel Gentoo wiki](https://wiki.gentoo.org/wiki/Intel) page before proceeding.

Then, to install support for the Vulkan API (will be functional only if you have a [Vulkan capable GPU](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility) and driver), execute:

	sudo emerge --ask --verbose dev-util/vulkan-tools dev-util/vulkan-headers media-libs/vulkan-layers media-libs/vulkan-loader

#### Nvidia

If you are using an Nvidia GPU, you will have to read through the [Nvidia-drivers Gentoo wiki](https://wiki.gentoo.org/wiki/NVIDIA/nvidia-drivers) page before proceeding.

Then, to install support for the Vulkan API (will be functional only if you have a [Vulkan capable GPU](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility) and driver), execute:

	sudo emerge --ask --verbose dev-util/vulkan-tools dev-util/vulkan-headers media-libs/vulkan-loader

### Installation

To install Lutris, execute:

	sudo emerge --ask --verbose games-util/lutris

## openSUSE

### Prerequisites

### Installation


## Ubuntu / Linux Mint / Other Ubuntu-based distributions:

### AMD / Intel:

**If you have Ubuntu 19.10 or newer:**
Enable 32 bit architecture (if you haven't already):

	sudo dpkg --add-architecture i386 

Install support for 32-bit games:

	sudo apt install libgl1-mesa-dri:i386

To install support for the Vulkan API  (will be functional only if you have a [Vulkan capable GPU](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility)) and 32-bit games, execute:

	sudo apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386

Reboot to apply changes.

### Nvidia:

To get the latest Nvidia drivers it is necessary to add the [Proprietary GPU Drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa):

	sudo add-apt-repository ppa:graphics-drivers/ppa

Enable 32 bit architecture (if you haven't already):

	sudo dpkg --add-architecture i386 

Update to refresh packages:

	sudo apt update

_**Warning**: Please ensure your graphics card is supported by the 430 driver before installing._
_For a list of supported GPUs click here: https://www.nvidia.com/Download/driverResults.aspx/149138/en-us_

Install the 430.40 driver:

	sudo apt install nvidia-driver-430 libnvidia-gl-430 libnvidia-gl-430:i386

To install support for the Vulkan API  (will be functional only if you have a [Vulkan capable GPU](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility)) and 32-bit games, execute:

	sudo apt install libvulkan1 libvulkan1:i386

Reboot to apply changes.


**If you have Ubuntu 18.04 Bionic Beaver or Ubuntu 18.10 Cosmic Cuttlefish:**

Add [kisak-mesa PPA](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa): 

	sudo add-apt-repository ppa:kisak/kisak-mesa

Enable 32 bit architecture (if you haven't already):

	sudo dpkg --add-architecture i386 

Upgrade your system:

	sudo apt update && sudo apt upgrade

Install support for 32-bit games:

	sudo apt install libgl1-mesa-glx:i386 libgl1-mesa-dri:i386

To install support for the Vulkan API  (will be functional only if you have a [Vulkan capable GPU](https://en.wikipedia.org/wiki/Vulkan_(API)#Compatibility)) and 32-bit games, execute:

	sudo apt install mesa-vulkan-drivers mesa-vulkan-drivers:i386


Reboot to apply changes.

_Note: Only Ubuntu 18.04 and higher is supported for AMD and Intel graphics._

_Note for Intel integrated graphics users: Only Skylake, Kaby Lake, and Coffee Lake offer full Vulkan support. Broadwell, Haswell and Ivy Bridge only offer partial support, which may not work with a lot of games. Sandy Bridge and older lack any Vulkan support whatsoever._
