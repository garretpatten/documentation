# Fedora Installation

## Configure Hardware Key Authentication

- [Configure YubiKey](https://blog.rtwm.io/2021/03/complete-u2f-yubikey-linux-mint-20-login-with-encrypted-home-folders/)
    - Steps:
        - `sudo dnf install pam pam-u2f pamu2fcfg`
        - `mkdir -p ~/.config/yubico`
        - `pamu2fcfg >> ~/.config/yubico/u2f_keys`
        - `sudo mkdir -p /etc/yubico`
        - `sudo cp ~/.config/yubico/u2f_keys /etc/yubico/u2f_keys`
        - `sudo chmod 644 /etc/yubico/u2f_keys`
        - Add the following line to pam.d files in bullets below: `auth sufficient pam_u2f.so authfile=/etc/yubico/u2f_keys`
            - sudo (for sudo usage)
            - gdm-password (for lock screen/login)
    - [PAM.d Information](https://www.digitalocean.com/community/tutorials/how-to-use-pam-to-configure-authentication-on-an-ubuntu-12-04-vps)
