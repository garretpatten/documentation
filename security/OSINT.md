# OSINT

## Browser Extensions

- `Foxy Proxy` - lets you quickly change the proxy server you are using to access the target website
- `User-Agent Switcher and Manager` - gives you the ability to pretend to be accessing the webpage from a different operating system or different web browser
- `Wappalyzer` - provides insights about the technologies used on the visited websites

## Common Ports

- 23: `telnet`
- 80: `http`
- 443: `https`
- 8080: `http`

## Content Discovery Tools

- `./sublist3r.py -d <URL>`
    - https://github.com/aboul3la/Sublist3r
- `curl -v <URL>` will callout to the IP in verbose mode revealing response headers
- `dirb <URL> <pathToWordlist>`
- `dnsrecon -t brt -d <URL>`
- `ffuf -w <pathToWordlist> -X <REQUEST_METHOD> -d <ARGUMENTS_TO_SEND_FUZZ_VAR> -u <URL>
    - `mr <PAGE_CONTENT_TO_VERIFY_RESULT>`
    - `fc <STATUS_CODE_TO_VERIFY_RESULTS>`
    - `w` flag can point to multiple things: `w pathToUsernames.txt:W1,pathToPasswords.txt:W2` which you can then plug into the `d` flag like "username=W1&password=W2"
- `gobuster dir --url <URL> -w <pathToWordlist>`
- `nmap -sV -sC <IP> -Pn` will execute a network mapper port scan

## DNS Tools

- `dig`
- `nslookup`
- `whois`

## Google Dorking

- `site:<website>` - returns results only from the specified website address
inurl
- `inurl:<value>` - returns results that have the specified word in the URL
filetype
- `filetype:<fileType>` - returns results which are a particular file extension
- `intitle:<value>` - returns results that contain the specified word in the title

## Network Tools

- `nc <URL> <Port>` - can function as a client that connects to a listening port; alternatively, it can act as a server that listens on a port of your choice
    - `netcat` support both TCP and UDP
- `nmap <URL>` - network mapper for port scanning
    - ARP Scan: `sudo nmap -PR -sn MACHINE_IP/24`
    - ICMP Echo Scan: `sudo nmap -PE -sn MACHINE_IP/24`
    - ICMP Timestamp Scan: `sudo nmap -PP -sn MACHINE_IP/24`
    - ICMP Address Mask Scan: `sudo nmap -PM -sn MACHINE_IP/24`
    - TCP SYN Ping Scan: `sudo nmap -PS22,80,443 -sn MACHINE_IP/30`
    - TCP ACK Ping Scan: `sudo nmap -PA22,80,443 -sn MACHINE_IP/30`
    - UDP Ping Scan: `sudo nmap -PU53,161,162 -sn MACHINE_IP/30`
    - `A`: Enables “aggressive” scanning. Presently this enables OS detection (`O`), version scanning (`sV`), script scanning (`sC`) and traceroute (`–traceroute`)
    - `sS`: Stealth mode scan
        - [Webpage](https://www.digitalocean.com/community/tutorials/nmap-switches-scan-types) walking through different `nmap` switches
- `ping -c <count> <URL>` - sends a packet to a remote system, and the remote system replies
- `traceroute <URL>` - traces the route taken by the packets from your system to another host
- `xsshunter` - a popular tool for blind XSS attacks that automatically captures cookies, URLs, page contents, and more

## Places to Look

- GitHub
- Amazon AWS
    - S3
        - Domains typically formatted as follows: `http(s)://{name}.s3.amazonaws.com`
        - One common automation method is by using the company name followed by common terms such as `{name}-assets`, `{name}-www`, `{name}-public`, `{name}-private`

## Tips & Tricks

- RCE payloads:
    - Unix-based
        - `whoami` (see what user the application is running under)
        - `ls` (list contents of current directory)
        - `ping` (can cause the application to hang)
        - `sleep` (for when ping is not installed)
        - `nc` (netcat can be used to spawn a reverse shell)
    - Windows
        - `whoami` (see what user the application is running under)
        - `dir` (list contents of current directory)
        - `ping` (can cause the application to hang
        - `timeout` (for when ping is not installed)
- `view-source:<website>` will render the source code in the browser window instead of the webpage
- SSRF giveaways:
    - When a full URL is used in a parameter in the address bar: `https://website.thm/form?server=http://server.website.thm/store`
    - A hidden URL field in a form: `value='<http://server.website.thm/store`>
    - A partial URL such as just the hostname: `https://website.thm/form?server=api`
    - Or perhaps only the path of the URL: `https://website.thm/form?dst=/forms/contact`
- In a cloud environment, it would be beneficial to try to access to the IP address `169.254.169.254`, which contains metadata for the deployed cloud server, including possibly sensitive information

## Website Content Discovery

- `favicon` - a small icon displayed in the browser's address bar or tab used for branding a website
    - [OWASP MD5 Favicon Hashes](https://wiki.owasp.org/index.php/OWASP_favicon_database)
- `robots.txt` - a document that tells search engines which pages they are and aren't allowed to show on their search engine results or ban specific search engines from crawling the website altogether
- `sitemap.xml` - gives a list of every file the website owner wishes to be listed on a search engine

## Wordlists

- [GTFOBins](https://gtfobins.github.io/) - a curated list of Unix binaries that can be used to bypass local security restrictions in misconfigured systems
- [SecLists](https://github.com/danielmiessler/SecLists) - a collection of multiple types of lists used during security assessments, collected in one place (usernames, passwords, URLs, sensitive data patterns, fuzzing payloads, web shells, etc)

## OSINT Search Engines

- [crackstation](https://crackstation.net/) - database of billions of hash to value results
- [crt.sh](https://crt.sh/) - certificates & subdomains
- [DNSdumpster](https://dnsdumpster.com/) - DNS search engine
- [Shodan.io](https://shodan.io/) - DNS search engine
- [Wayback Machine](https://archive.org/web/) - webpage archive
