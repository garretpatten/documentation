# Arch Installation Guide

## Pre-Installation: Connect to WiFi

- Show IP Address Info: `ip addr show`
- Get available WiFi networks: `iwctl station wlan0 get-networks`
- Connect to WiFi Network: `iwctl station wlan0 connect <network> --passphrase <“password”>`
    - If WiFi passphrase has special characters, you can avoid having to escape those special characters by omitting the `-passphrase` flag. The system will prompt you for the WiFi passphrase, and you can enter it as normal.
- Verify Connection by Checking IP Address: `ip addr show`

*Note: You can first run `iwctl` and then enter commands starting with `station`*

## Installation

### Easy Install

- `archinstall`
- TODO: Fill out options to select

### Manual Install

- TODO

## Additional Resources

### Video Walkthrough

- [Arch Linux Installation Guide 2024: An Easy to Follow Tutorial](https://www.youtube.com/watch?v=FxeriGuJKTM&t=753s)
