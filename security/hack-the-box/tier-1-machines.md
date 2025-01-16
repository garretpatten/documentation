# Appointment

- SQL - Structured Query Language
- PII - Personally Identifiable Information
- `nmap -sV -sC {target_IP}` will return all services and their versions and also all available scripts
- 443 is the default port for HTTPS protocol
- 404 error code - "Not Found"
- `gobuster` - a tool used to brute-force URIs (including directories and files as well as DNS subdomains) written in Go
    - `dir` - Gobuster switch to specify search for directories (instead of subdomains)
    - Example: `gobuster dir --url <http://10.129.91.77> --wordlist ~/wordlists/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt`
    - Alternatives to Gobuster: `dirbuster` and `dirb`

# Sequel

- `sql -h {target_IP} -u {username}` can be used to test passwordless logins on mySql servers
- `SHOW DATABASES;` and `USE {database};`
- `SHOW TABLES;` and `SELECT * FROM {table};`

# Crocodile

- `nmap -sC` employs the use of default scripts during a scan
- FTP Code 230 is returned to signify Anonymous FTP login allowed"
- Wappalyzer is a useful browser extension to analyze a web site's technologies
- `gobuster -x` allows you to specify specific file types to search for on an IP address (`html,php` for example)

# Responder

- TODO
