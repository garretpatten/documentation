# Dual-Boot a Macbook

## Directions

- Partition hard drive
    - 100 gb for new OS
    - 16 gb for SWAP (this amount should match RAM)
- Install `rEFInd` --it allows for easy dual boot on startup
- Boot into Recovery mode for mac and run:
    - `csrutil disable`
- Restart and verify `rEFInd` works as expected
- Boot into bootable usb with linux ISO
    - Go through install process
    - Select the partitioning properly (use memory allocations to determine)
        - New OS partition will get EXT 4 format
        - SWAP partition will get SWAP format
- Finish installation, reboot, and verify the installation works
- Reinstall `rEFInd`
- Boot into Recovery mode for mac and run:
    - `csrutil enable`
- Reboot

## Video Walkthrough

- [How to dual boot Linux and macOS on a Mac](https://www.youtube.com/watch?v=GcdhJfe3aP8)
