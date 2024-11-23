# Vioneta Operating System

Vioneta Operating System is a Linux based operating system optimized to host [Vioneta](https://www.vioneta.com) and its [Add-ons](https://www.vioneta.com/addons/).

Vioneta Operating System uses Docker as its container engine. By default it deploys the Vioneta Supervisor as a container. Vioneta Supervisor in turn uses the Docker container engine to control Vioneta Core and Add-Ons in separate containers. Vioneta Operating System is **not** based on a regular Linux distribution like Ubuntu. It is built using [Buildroot](https://buildroot.org/) and it is optimized to run Vioneta. It targets single board compute (SBC) devices like the Raspberry Pi or ODROID but also supports x86-64 systems with UEFI.

## Features

- Lightweight and memory-efficient
- Minimized I/O
- Over The Air (OTA) updates
- Offline updates
- Modular using Docker container engine

## Supported hardware

- Raspberry Pi
- Hardkernel ODROID
- Asus Tinker Board
- Generic x86-64 (e.g. Intel NUC)
- Virtual appliances

See the full list and specific models [here](./Documentation/boards/README.md)

## Getting Started

If you just want to use Vioneta the official [getting started guide](https://www.vioneta.com/getting-started/) and [installation instructions](https://www.vioneta.com/hassio/installation/) take you through how to download Vioneta Operating System and get it running on your machine.

If you're interested in finding out more about Vioneta Operating System and how it works read on...

## Development

If you don't have experience with embedded systems, Buildroot or the build process for Linux distributions it is recommended to read up on these topics first (e.g. [Bootlin](https://bootlin.com/docs/) has excellent resources).

The Vioneta Operating System documentation can be found on the [Vioneta Developer Docs website](https://developers.vioneta.com/docs/operating-system).

### Components

- **Bootloader:**
  - [GRUB](https://www.gnu.org/software/grub/) for devices that support UEFI
  - [U-Boot](https://www.denx.de/wiki/U-Boot) for devices that don't support UEFI
- **Operating System:**
  - [Buildroot](https://buildroot.org/) LTS Linux
- **File Systems:**
  - [SquashFS](https://www.kernel.org/doc/Documentation/filesystems/squashfs.txt) for read-only file systems (using LZ4 compression)
  - [ZRAM](https://www.kernel.org/doc/Documentation/blockdev/zram.txt) for `/tmp`, `/var` and swap (using LZ4 compression)
- **Container Platform:**
  - [Docker Engine](https://docs.docker.com/engine/) for running Vioneta components in containers
- **Updates:**
  - [RAUC](https://rauc.io/) for Over The Air (OTA) and USB updates
- **Security:**
  - [AppArmor](https://apparmor.net/) Linux kernel security module

### Development builds

The Development build GitHub Action Workflow is a manually triggered workflow
which creates Vioneta OS development builds. The development builds are
available at [https://os-artifacts.vioneta.com/index.html](https://os-artifacts.vioneta.com/index.html).
