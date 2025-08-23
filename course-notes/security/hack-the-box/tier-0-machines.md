# Tier 0 Machines

## Meow

- VM - Virtual Machine
- Terminal - used to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection; also known as the console or shell
- Hack the Box labs use the OpenVPN service to form its VPN connections
- `tun` - the abbreviated name for a tunnel interface in the output of a VPN boot-up sequence
- `ping` - tool used to test connections to targets with an ICMP echo request
- `nmap` - the name of the most common tool for finding open ports on a target

## Fawn

- FTP - File Transfer Protocol
- The FTP service usually listens on port 21
- `sftp` - the acronym for the secure version of FTP
- `nmap -sV {target_IP} -Pn` will scan for services and version on ports and override ping probes being blocked
- anonymous - the username that is used over FTP when you want to log in without having an account

## Dancing

- SMB - Server Message Block
- The SMB service usually listens on port 445
- `l` - flag/switch used to list the contents of a share with the SMB tool
- `get` - SMB command to download files
- There is an SMB client on MacOS: Finder > Go > Connect to Server > smb://{target_IP}

## Redeemer

- `p-` can be used to scan *all* ports on a target
- If an `nmap` scan is slow, use `-min-rate 5000` or `T5` to speed it up
- Redis is an in-memory database
- Redis usually listens on port 6379
- `redis-cli` is the command-line utility used to interact with Redis databases
- `redis-cli -h {target_IP}` can be used to connect to the Redis database on the host IP (assuming that database is using the default port)
- Once connected to the Redis server, `info` will display information and statistics about the server
- `select` is used to select the desired database in Redis
- Once a database has been selected, `keys *` will output all the keys in the database
- `get {key}` can then be used to print out the value of the key
