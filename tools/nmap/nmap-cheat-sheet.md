# Nmap Cheat Sheet

## Getting Started

- **Nmap** (Network Mapper) is a free and open source network mapper utility
  for network discovery and security auditing
- Basic scan: `nmap <target>`
- Scan multiple targets: `nmap <target1> <target2> <target3>`
- Scan IP range: `nmap 192.168.1.1-254`
- Scan subnet: `nmap 192.168.1.0/24`
- Scan from file: `nmap -iL <file>`
- Save output: `-oN <file>` (normal), `-oX <file>` (XML), `-oG <file>`
  (grepable), `-oA <file>` (all formats)

## Scan Types

### TCP Scans

- **SYN scan** (stealth): `-sS` (requires root, default for root)
  - Half-open scan, doesn't complete TCP handshake
- **TCP connect scan**: `-sT` (default for non-root)
  - Completes full TCP handshake
- **TCP ACK scan**: `-sA`
  - Determines if ports are filtered
- **TCP window scan**: `-sW`
  - Similar to ACK scan but can detect open ports
- **TCP Maimon scan**: `-sM`
  - Sends FIN/ACK packets

### UDP Scans

- **UDP scan**: `-sU`
  - Scans UDP ports (slower than TCP)
- **UDP scan with version detection**: `-sUV`

### Other Scans

- **Ping scan** (host discovery only): `-sn`
- **No port scan**: `-sn` (formerly `-sP`)
- **List scan**: `-sL` (just lists targets, doesn't scan)
- **IP protocol scan**: `-sO`
- **Idle scan**: `-sI <zombie_host>`
- **FIN scan**: `-sF`
- **NULL scan**: `-sN`
- **Xmas scan**: `-sX` (sets FIN, PSH, URG flags)

## Host Discovery

- Skip host discovery: `-Pn` (treat all hosts as online)
- Only host discovery: `-sn` (no port scan)
- Disable DNS resolution: `-n`
- Enable DNS resolution: `-R` (always resolve)
- Use system DNS: `--system-dns`
- Specify DNS servers: `--dns-servers <servers>`
- ARP ping: `-PR` (default for local networks)
- ICMP ping: `-PE` (echo request)
- TCP SYN ping: `-PS <port_list>`
- TCP ACK ping: `-PA <port_list>`
- UDP ping: `-PU <port_list>`
- SCTP ping: `-PY <port_list>`
- ICMP timestamp: `-PP`
- ICMP netmask: `-PM`

## Port Specification

- Scan specific ports: `-p 80,443,8080`
- Scan port range: `-p 1-1000`
- Scan all ports: `-p-` or `-p 1-65535`
- Scan top ports: `--top-ports <number>`
- Scan common ports: `-F` (fast scan, 100 most common ports)
- Exclude ports: `--exclude-ports <port_list>`
- Scan UDP ports: `-sU -p <ports>`

## Service and Version Detection

- Version detection: `-sV`
- Version detection intensity: `--version-intensity <0-9>` (default 7)
- Light version scan: `--version-light` (intensity 2)
- All version probes: `--version-all` (intensity 9)
- Version trace: `--version-trace` (debugging)

## OS Detection

- OS detection: `-O`
- OS detection with version: `-O --osscan-guess`
- Aggressive OS detection: `-A` (includes OS detection, version detection,
  script scanning, traceroute)
- OS detection limit: `--osscan-limit` (only scan hosts with open/closed ports)

## Script Scanning

- Default scripts: `-sC` or `--script=default`
- Specific script: `--script <script_name>`
- Multiple scripts: `--script <script1>,<script2>`
- Script category: `--script <category>`
- All scripts: `--script=all` (use with caution)
- Script help: `--script-help <script_name>`
- Script args: `--script-args <args>`
- Script trace: `--script-trace`
- Update script database: `nmap --script-updatedb`

### Common Script Categories

- **auth**: Authentication bypass scripts
- **broadcast**: Network discovery scripts
- **brute**: Brute force attack scripts
- **default**: Default scripts (safe and useful)
- **discovery**: Host and service discovery
- **dos**: Denial of service scripts
- **exploit**: Exploit scripts
- **external**: Scripts using external services
- **fuzzer**: Fuzzing scripts
- **intrusive**: Intrusive scripts (may crash services)
- **malware**: Malware detection
- **safe**: Safe scripts (won't crash services)
- **version**: Version detection enhancement
- **vuln**: Vulnerability detection

### Useful Scripts

- SMB enumeration: `--script smb-enum-shares,smb-enum-users`
- HTTP enumeration: `--script http-enum,http-headers,http-methods`
- SSH enumeration: `--script ssh-hostkey,ssh-auth-methods`
- FTP enumeration: `--script ftp-anon,ftp-bounce`
- DNS enumeration: `--script dns-brute,dns-srv-enum`
- Vulnerability scan: `--script vuln`
- Safe scripts: `--script safe`

## Timing and Performance

- Timing template: `-T<0-5>` (0=paranoid, 1=sneaky, 2=polite, 3=normal,
  4=aggressive, 5=insane)
- Default: `-T3` (normal)
- Aggressive: `-T4` (faster, may be detected)
- Insane: `-T5` (very fast, likely to be detected)
- Min parallel hosts: `--min-hostgroup <size>`
- Max parallel hosts: `--max-hostgroup <size>`
- Min parallel probes: `--min-parallelism <num>`
- Max parallel probes: `--max-parallelism <num>`
- Host timeout: `--host-timeout <time>`
- Max retries: `--max-retries <num>`
- Initial RTT timeout: `--initial-rtt-timeout <time>`
- Min RTT timeout: `--min-rtt-timeout <time>`
- Max RTT timeout: `--max-rtt-timeout <time>`

## Firewall/IDS Evasion

- Fragment packets: `-f` (fragment IP packets)
- Fragment packets (16 bytes): `-ff`
- MTU: `--mtu <size>`
- Decoy scan: `-D <decoy1,decoy2,ME>` (spoof source IPs)
- Spoof source IP: `-S <spoofed_ip>`
- Spoof source port: `-g <port>` or `--source-port <port>`
- Data length: `--data-length <length>` (append random data)
- Randomize hosts: `--randomize-hosts`
- Randomize ports: `--randomize-ports`
- TTL: `--ttl <value>`
- Bad checksum: `--badsum` (test firewall response)
- IP options: `--ip-options <options>`

## Output Options

- Normal output: `-oN <file>`
- XML output: `-oX <file>`
- Grepable output: `-oG <file>`
- All formats: `-oA <file>`
- Verbose: `-v` (more detail)
- Very verbose: `-vv` (even more detail)
- Debug: `-d` (debugging info)
- More debug: `-dd` (more debugging)
- Reason: `--reason` (show reason for port state)
- Stats: `--stats-every <time>` (periodic stats)
- Append output: `--append-output`

## Common Scan Examples

### Basic Scans

- Quick scan: `nmap -F <target>`
- Quick scan top ports: `nmap --top-ports 20 <target>`
- Scan common ports: `nmap -F <target>`
- Full port scan: `nmap -p- <target>`
- Scan specific ports: `nmap -p 22,80,443 <target>`

### Stealth Scans

- SYN scan: `nmap -sS <target>`
- Stealth scan with version: `nmap -sS -sV <target>`
- Stealth scan with OS detection: `nmap -sS -O <target>`

### Comprehensive Scans

- Aggressive scan: `nmap -A <target>`
- Full scan with scripts: `nmap -sC -sV -O <target>`
- UDP scan: `nmap -sU <target>`
- UDP scan with version: `nmap -sU -sV <target>`

### Network Scans

- Scan local network: `nmap -sn 192.168.1.0/24`
- Scan network with version: `nmap -sV 192.168.1.0/24`
- Scan network with scripts: `nmap -sC 192.168.1.0/24`

### Service-Specific Scans

- HTTP enumeration: `nmap --script http-enum,http-headers -p 80,443 <target>`
- SMB enumeration: `nmap --script smb-enum-shares,smb-enum-users -p 445 <target>`
- SSH scan: `nmap --script ssh-hostkey,ssh-auth-methods -p 22 <target>`
- FTP scan: `nmap --script ftp-anon,ftp-bounce -p 21 <target>`

### Vulnerability Scans

- Vulnerability scan: `nmap --script vuln <target>`
- Safe vulnerability scan: `nmap --script vuln --script-args=unsafe=0 <target>`

## Useful Tips

- Use `sudo` for SYN scans and OS detection (requires root)
- Combine options: `nmap -sS -sV -O -p- <target>`
- Save all output formats: `nmap -oA scan <target>`
- Use verbose mode for troubleshooting: `nmap -vv <target>`
- Update NSE scripts regularly: `nmap --script-updatedb`
- Use timing templates for different scenarios
- Fragment packets to evade firewalls
- Use decoy scans to hide your IP
- Combine with other tools for comprehensive reconnaissance
