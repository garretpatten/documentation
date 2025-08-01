# Windows Subsystem for Linux

## Getting Started

### WSL Installation

- Install Guide: <https://learn.microsoft.com/en-us/windows/wsl/install>
- `wsl --install`
- Restart

### Distro Installation

#### Kali Install

- `wsl --install -d kali-linux`
    - username
    - password
    - password confirm
- `wsl --setdefault kali-linux`
- Kali Setup Guide: <https://www.kali.org/docs/general-use/metapackages/>
- `wsl sudo apt update`
- `wsl sudo apt full-upgrade -y`
- `wsl sudo apt install -y kali-linux-defaults`
    - A few Enter keypresses to confirm config
- If desktop environment is desired:
    - `wsl sudo apt install -y kali-desktop-kde`
    - `wsl sudo apt install -y kali-desktop-gnome`
    - `wsl sudo apt install -y kali-desktop-xfce`

### Distro Removal

- `wsl -l` to see a list of installed distro names
- `wsl --unregister <DistroName>`

## WSL Filesystem

Windows Subsystem for Linux runs on a Linux filesystem mounted at `/mnt`. This means if I create a Linux user called `garret`, the home directory of that user will live at the following: `/mnt/wslg/distro/home/garret`.

### Running WSL vs Opening Linux Terminal

- When PowerShell is opened and `wsl` is run, a Linux terminal in the default distro will start at the working directory the Windows user in context was already operating in. So, if my Windows user `garre` runs `wsl` in PowerShell and then `pwd`, it will print: `/mnt/c/Users/garre`. Running WSL this way gives you access to the computer’s entire file system — both Windows and Linux.
- Alternatively, when a Linux terminal is opened through the Windows UI, it will initiate at `/mnt/wslg/distro/home/garret`. This terminal, however, will only have access to the Linux file system. So, if my user `garre` uses the Windows UI to open a Linux terminal before running `pwd`, it will print: `/home/garret`.

## WSL Performance

### WSL vs. Bare Metal Linux (Performance)

- The performance of Ubuntu Linux run using the Windows Subsystem for Linux 2 ([WSL2](https://www.techradar.com/news/running-linux-on-windows-10-just-got-a-little-less-janky)) under the [Windows 11](https://www.techradar.com/news/windows-11-home-and-pro) release was a close match to the performance of the distro run on bare metal
    - *Phoronix* tried to gauge the improvements of the WSL2 subsystems of the upcoming Windows release, by pitting it against native [Ubuntu 20.04](https://www.techradar.com/reviews/ubuntu-2004-lts-focal-fossa) and the Ubuntu 21.10 installations
    - “Out of 130 tests in total, Windows 11 WSL2 Ubuntu 20.04 LTS managed to run at 94% the speed of bare metal Ubuntu 20.04 LTS on the same system,” observes *Phoronix*.
- Source: <https://www.techradar.com/news/windows-11-wsl-2-is-almost-as-quick-as-running-linux-natively>

## Windows/WSL System Guide

- TODO: How should the system be used with regard to Windows and WSL
    - TODO: GUI applications managed with winget and all CLI tooling/development on WSL
        - TODO: Once setup is decided, bring to GitHub setup scripts repo
