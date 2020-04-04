# TODO.md

This is a list of what we are planning on adding in the future. If something is ~~struckthrough~~, it means that we have added it or unfortunately cancelled it.

## [awesome-gnu-linux-gaming.md](/awesome-gnu-linux-gaming.md)

- Add [FeralInteractive / gamemode](https://github.com/FeralInteractive/gamemode)
- Add [flightlessmango / MangoHud](https://github.com/flightlessmango/MangoHud)
- Add [benjamimgois / GOverlay](https://github.com/benjamimgois/goverlay)
- Add [DadSchoorse / vkBasalt](https://github.com/DadSchoorse/vkBasalt)
- Add AMD GPU hacks
	- [ACO compiler](https://wiki.archlinux.org/index.php/AMDGPU#ACO_compiler)
	- [Custom Xorg configuration (eliminate screen tearing)](https://wiki.archlinux.org/index.php/AMDGPU#Xorg_configuration)
	- [Overclocking](https://wiki.archlinux.org/index.php/AMDGPU#Overclocking)
- Add Nvidia GPU hacks
	- [Reference Arch wiki: NVIDIA / Tips and tricks](https://wiki.archlinux.org/index.php/NVIDIA/Tips_and_tricks)
- Custom kernel
	- [CK patchsets](http://ck.kolivas.org/)
	- [ZEN/Liquorix patchsets](https://github.com/zen-kernel/zen-kernel)
	- [Post Factum patchsets](https://gitlab.com/post-factum/pf-kernel)
- Add references
	- https://www.icculus.org/lgfaq/gamelist.php

## [installing-lutris.md](/installing-lutris.md)

- ~~Add [Alpine](https://alpinelinux.org/)~~
	- Update [Alpine](https://alpinelinux.org)
- ~~Add [Arch](https://www.archlinux.org/)~~
- Add [CentOS](https://www.centos.org/)
- Add [Clear](https://clearlinux.org/)
- Add [Debian](https://www.debian.org/)
- ~~Add [Fedora](https://getfedora.org/)~~
- ~~Add [Gentoo](https://www.gentoo.org/)~~
- Add [Mageia](https://www.mageia.org/en/)
- ~~Add [NixOS](https://nixos.org/)~~
	- Retract NixOS
	- Add [NixOS (example)](#nixos)
- ~~Add [openSUSE](https://software.opensuse.org/)~~
- Add [Slackware](http://www.slackware.com/)
- Add [Solus](https://getsol.us/home/)
- Revamp [*buntu](https://ubuntu.com/download/flavours)
- ~~Add [Void](https://voidlinux.org/)~~
- Add Others
	- ~~Add [Flatpak](https://flatpak.org/)~~
	- Add [Tarball](https://lutris.net/releases/)
	- Add [Source](https://github.com/lutris/lutris)

### NixOS

### Prerequisites

#### AMD / Intel

To install support for the Vulkan API and its tools, your `*.nix` (e.g. `configuration.nix`) must have the following as **system packages**:

- `pkgs.vulkan-headers`;
- `pkgs.vulkan-loader`;
- `pkgs.vulkan-tools`;
- `pkgs.vulkan-validation-layers`.

Your `*.nix` file will look similar to this: 

```nix
environment.systemPackages = [ pkgs.vulkan-headers pkgs.vulkan-loader pkgs.vulkan-tools pkgs.vulkan-validation-layers ];
```

Then, execute the following command as root:

```bash
nixos-rebuild switch
```

Then proceed to the [installation](#installation-4).

#### Nvidia

To install support for the Vulkan API and its tools, you will have to install the **proprietary** drivers.

To install them, you will have to refer to the [NixOS wiki](https://nixos.wiki/wiki/Nvidia).

Then, your `*.nix` (e.g. `configuration.nix`) must have the following as **system packages**:

- `pkgs.vulkan-headers`;
- `pkgs.vulkan-loader`;
- `pkgs.vulkan-tools`;
- `pkgs.vulkan-validation-layers`.

```nix
environment.systemPackages = [ pkgs.vulkan-headers pkgs.vulkan-loader pkgs.vulkan-tools pkgs.vulkan-validation-layers ];
```

At last, execute the following command as root:

```bash
nixos-rebuild switch
```

Then, proceed to the [installation](#installation-4).

### Installation

To install Lutris, your `*.nix` (e.g. `configuration.nix`) must have Lutris (`pkgs.lutris-unwrapped`) as a **system package**

Your `*.nix` file will look similar to this:

```nix
environment.systemPackages = [ pkgs.lutris-unwrapped ];
```

Then, execute the following command as root:

```bash
nixos-rebuild switch
```

