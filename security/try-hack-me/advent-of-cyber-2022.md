# Advent of Cyber 2022

## Day 1

- Security frameworks are documented processes that define policies and procedures organizations should follow to establish and manage security controls
    - they are blueprints for identifying and managing the risks they may face and the weaknesses in place that may lead to an attack
- National Institute of Standards and Technology (NIST) Cybersecurity Framework (CSF)
    - Identify
    - Protect
    - Detect
    - Respond
    - Recover
- International Organization of Standardization (ISO) 27000 Series
    - ISO 27001 and 27002 standards are commonly known for cybersecurity and outline the requirements and procedures for creating, implementing and managing an information security management system (ISMS)
- MITRE ATT&CK Framework
    - Adversary plans of attack can be understood through the behaviors, methods, tools and strategies established for an attack, commonly known as Tactics, Techniques and Procedures (TTPs)
- Cyber Kill Chain
    - Developed by Lockheed Martin, it describes the stages commonly followed by cyber attacks and security defenders can use the framework as part of intelligence-driven defense
    - 7 Stages:
        - Recon
        - Weaponization
        - Delivery
        - Exploitation
        - Installation
        - Command & Control
        - Actions on Objectives
- Unified Kill Chain
    - The Unified Kill Chain can be described as the unification of the MITRE ATT&CK and Cyber Kill Chain frameworks
    - It describes 18 phases of attack based on Tactics, Techniques and Procedures (TTPs)
    - 3 Cycles which contain a series of phases:
        - Cycle 1: In
            - Reconnaissance
            - Weaponization
            - Delivery
            - Social Engineering
            - Exploitation
            - Persistance
            - Defense Evasion
            - Command & Control
        - Cycle 2: Through
            - Pivoting
            - Discovery
            - Privilege Escalation
            - Execution
            - Credential Access
            - Lateral Movement
        - Cycle 3: Out
            - Collection
            - Exfiltration
            - Impact
            - Objectives

## Day 2

- Log files are files that contain historical records of events and other data form an application
    - Examples include:
        - Login attempts or failures
        - Trafic on a network
        - Things (website URLs, files, etc) that have been accessed
        - Password changes
        - Application errors (used in debugging)
        - etc
- Log files typically include:
    - Event
    - Timestamp of event
    - Service logging the event
- Log files can quickly contain many events and hundreds, if not thousands, of entries
- The difficulty in analysing log files is separating useful information from useless
    - Tools such as Splunk are software solutions known as Security Information and Event Management (SIEM) is dedicated to aggregating logs for analysis
- Grep is a command dedicated to searching for a given text in a file
    - Grep takes a given input (a text or value) and searches the entire file for any text that matches our input
- Here are some ideas for things you may want to use grep to search a log file for:
    - A name of a computer
    - A name of a file
    - A name of a user account
    - An IP address
    - A certain timestamp or date
- `grep -r` will recursively search through all files in the current directory
- `grep -i something myFile.log` will search for a case insensitive match to "something" in myFile.log
- `grep -E someRegex myFile.log` will search for a regex match to "someRegex" in myFile.log

## Day 3

- OSINT (open source intelligence) is gathering and analyzing publicly available data for intelligence purposes, which includes information collected from the internet, mass media, specialist journals and research, photos, and geospatial information
    - The information can be accessed via the open internet (indexed by search engines), closed forums (not indexed by search engines) and the dark web
- OSINT Techniques:
    - **Google Dorking** involves using specialist search terms and advanced search operators to find results that are not usually displayed using regular search terms
        - You can use them to search specific file types, cached versions of a particular site, websites containing specific text etc
            - `inurl`: Searches for a specified text in all indexed URLs. For example, inurl:hacking will fetch all URLs containing the word "hacking"
            - `filetype`: Searches for specified file extensions. For example, filetype:pdf "hacking" will bring all pdf files containing the word "hacking"
            - `site`: Searches all the indexed URLs for the specified domain. For example, site:tryhackme.com will bring all the indexed URLs from [tryhackme.com](http://tryhackme.com/)
            - `cache`: Get the latest cached version by the Google search engine. For example, cache:tryhackme.com
        - For example, you can use the dork `site:github.com "DB_PASSWORD"` to search only in [github.com](http://github.com/) and look for the string DB_PASSWORD (possible database credentials)
    - **WHOIS** database stores public domain information such as registrant (domain owner), administrative, billing and technical contacts in a centralised database
        - The database is publicly available for people to search against any domain and enables acquiring Personal Identifiable Information (PII) against a company, like an email address, mobile number etc., of technical contact
    - The **robots.txt** is a publicly accessible file created by the website administrator and intended for search engines to allow or disallow indexing of the website's URLs
        - All websites have their robots.txt file directly accessible through the domain's main URL
        - It is a kind of communication mechanism between websites and search engine crawlers
    - **Breach Database Search**
        - Major social media and tech giants have suffered data breaches in the past; as a result, the leaked data is publicly available and, most of the time contains PII like usernames, email addresses, mobile numbers and even passwords
        - **HaveIBeenPwned** is a great resource
    - **Searching GitHub Repos**
        - GitHub is a renowned platform that allows developers to host their code through version control; a common flaw by developers is that the privacy of the repository is set as public, which means anyone can access it -- these repositories contain complete source code and, most of the time, include passwords, access tokens, etc.

## Day 4

- Scanning is a set of procedures for identifying live hosts, ports, and services, discovering the operating system of the target system, and identifying vulnerabilities and threats in the network
- Types:
    - Passive Scanning:
        - This method involves scanning a network without directly interacting with the target device (server, computer etc.)
        - Passive scanning is usually carried out through packet capture and analysis tools like Wireshark; however, this technique only provides basic asset information like OS version, network protocol etc., against the target
    - Active Scanning:
        - Active scanning is a scanning method whereby you scan individual endpoints in an IT network to retrieve more detailed information
        - The active scan involves sending packets or queries directly to specific assets rather than passively collecting that data by "catching" it in transit on the network's traffic
        - Active scanning is an immediate deep scan performed on targets (a single endpoint or a network of endpoints) to get detailed information
- Techniques:
    - Network Scanning:
        - A network is usually a collection of interconnected hosts or computers to share information and resources
        - Network scanning helps to discover and map a complete network, including any live computer or hosts, open ports, IP addresses, and services running on any live host and operating system
            - Once the network is mapped, an attacker executes exploits as per the target system and services discovered
    - Port Scanning:
        - A port is a number assigned to uniquely identify a connection endpoint and to direct data to a specific service; at the software level, within an operating system, a port is a logical construct that identifies a specific process or a type of network service
        - Port scanning is a conventional method to examine open ports in a network capable of receiving and sending data
        - Types of Ports:
            - Closed Ports: The host is not listening to the specific port
            - Open Ports: The host actively accepts a connection on the specific port
            - Filtered Ports: The port is open; however, the host is not accepting connections or accepting connections as per certain criteria like specific source IP address
    - Vulnerability Scanning: The vulnerability scanning proactively identifies the network's vulnerabilities in an automated way that helps determine whether the system may be threatened or exploited
- Scanning Tools:
    - `Network Mapper (nmap)` is a popular tool used to carry out port scanning, discover network protocols, identify running services, and detect operating systems on live hosts
        - A **TCP SYN Scan** gets the list of live hosts and associated ports on the hosts without completing the TCP three-way handshake and making the scan a little stealthier: `nmap -sS <ipAddress>`
        - A **Ping Scan** allows scanning the live hosts in the network without going deeper and checking for ports services etc: `nmap -sn <ipAddress>`
        - An **Operating System Scan** allows scanning of the type of OS running on a live host: `nmap -sV <ipAddress>`
    - `Nikto` is open-source software that allows scanning websites for vulnerabilities; and, it enables looking for subdomains, outdated servers, debug messages etc., on a website: `nikto -host <ipAddress>`

## Day 5

- The need for remote administration of computer systems led to the development of various software packages and protocols, like:
    - **SSH (Secure Shell)**: initially used in Unix-like systems for remote login -- it provides the user with a command-line interface (CLI) that can be used to execute commands
    - **RDP (Remote Desktop Protocol)**: also known as Remote Desktop Connection (RDC) or simply Remote Desktop (RD) -- it provides a graphical user interface (GUI) to access an MS Windows system
        - When using Remote Desktop, the user can see their desktop and use the keyboard and mouse as if sitting at the computer
    - **VNC (Virtual Network Computing)**: it provides access to a graphical interface which allows the user to view the desktop and (optionally) control the mouse and keyboard
        - VNC is available for any system with a graphical interface, including MS Windows, Linux, and even macOS, Android and Raspberry Pi
- Authentication refers to the process where a system validates your identity
    - The process starts with the user claiming a specific unique identity (like a username)
    - The process is usually achieved through one of the following:
        - Something You Know (like a password)
        - Something You Have (like a MFA token)
        - Something You Are (biometric auth)
- Remote access services typically rely on a password or private key file for authentication
- Attacks on Passwords:
    - Shoulder Surfing
    - Password Guessing
    - Dictionary Attack
    - Brute Force Attack
- RockYou's list of breached passwords is a good example for a Dictionary Attack
    - RockYou’s word list contains more than 14 million unique passwords
- Tools exist for trying common passwords or entries from a word list, like **THC Hydra**
    - Hydra supports many protocols, including SSH, VNC, FTP, POP3, IMAP, SMTP, and all methods related to HTTP
    - Usage: `hydra -l username -P wordlist.txt <server> service`
        - `l` points to the login name
        - `P` points to the list of candidate passwords
        - `<server>` is the hostname of IP Address of the target
        - `<service>` indicates the service in which you are trying to launch the dictionary attack
            - Example parameters: `ssh`, `rdp`, `vnc`, `ftp`, `pop3`, etc
        - Examples:
            - `hydra -l mark -P /usr/share/wordlists/rockyou.txt <ipAddress> ssh`
            - `hydra -l mark -P /usr/share/wordlists/rockyou.txt ssh://<ipAddress>`
    - Optional Hydra flags
        - `V` or `vV` (verbose) makes Hydra show the username and password combinations being tried
        - `d` (debuggin) provides more detailed information about what’s happening
            - The debugging output can save you much frustration; for instance, if Hydra tries to connect to a closed port and timing out, `d` will reveal this immediately
- Many clients can be used to connect to a VNC server, one example is **Remmina**

## Day 6

- Email analysis is the process of extracting the email header information to expose the email file details
    - The email header contains the technical details of the email like sender, recipient, path, return address and attachments
- Two main concerns with Email Analysis:
    - Security issues: Identifying suspicious/abnormal/malicious patterns in emails
    - Performance issues: Identifying delivery and delay issues in emails
- Social engineering: Social engineering is the psychological manipulation of people into performing or divulging information by exploiting weaknesses in human nature
    - These "weaknesses" can be curiosity, jealousy, greed, kindness, and willingness to help someone
- Phishing: Phishing is a sub-section of social engineering delivered through email to trick someone into either revealing personal information and credentials or executing malicious code on their computer
    - Phishing emails will usually appear to come from a trusted source, and they will include content that tries to tempt or trick people into downloading software, opening attachments, or following links to a bogus website
- Structure of an Email Header:
    - From
    - To
    - Date
    - Subject
    - Return Path: The return address of the reply
    - Domain Key and DKIM Signatures: Email signatures provided by email services to identify and authenticate emails
    - SPF: Shows the server that was used to send the email
    - Message-ID: Unique ID of the email
    - MIME-Version: Used MIME version (which helps to understand the delivered non-text contents/attachments
    - X-Headers: The receiver mail providers usually add these fields (provided info is usually experimental and varies by mail provider)
    - X-Received: Mail servers that the email went through
    - X-Spam Status: Spam score of the email
    - X-Mailer: Email client name
- Important Email Header Fields (for Quick Analysis)
    - Do the From, To, and CC fields contain valid addresses? (They should)
    - Are the From and To fields the same? (They should not be)
    - Are the From and Return Path fields the same? (They should be)
    - Was the email sent from the correct server? (Email should come from the official mail servers of the sender)
    - Does the "Message-ID" field exist and is it valid? (It should be populated and not malformed)
    - Do the hyperlinks redirect to suspicious/abnormal sites? (They should not)
    - Do the attachments consist of or contain Malware? (They should not - look for file hashes marked as suspicious/malicious)
- The `emlAnalyzer` tool helps to view email details in a clearer format -- it can show the headers, body, embedded URLs, plaintext and HTML data, and attachments
    - `i`: path to file (to analyze)
    - `-header`: show headers
    - `u`: show URLs
    - `-text`: show cleartext data
    - `-extract-all`: extract all attachments
- Some OSINT tools to check email repudiation like https://emailrep.io/
- Other useful OSINT tools:
    - VirusTotal: a service that provides a cloud-based detection toolset and sandbox environment
    - InQuest: a service that provides network and file analysis by using threat analytics
    - [IPinfo.io](http://ipinfo.io/): a servicethat provides detailed information about an IP address by focusing on geolocation data and service provider
    - Talos Reputation: An IP reputation check service is provided by Cisco Talos
    - [Urlscan.io](http://urlscan.io/): a service that analyzes websites by simulating regular user behavior
    - Browserling: a browser sandbox is used to test suspicious/malicious links
    - Wannabrowser: a browser sandbox is used to test suspicious/malicious links

## Day 7

- CyberChef is a web-based application - used to slice, dice, encode, decode, parse and analyze data or files
    - First you choose a file as input
    - Then, you choose operations and add them to the Recipe
    - When the Recipe is set, you can bake the recipe (run the operations) that have been selected to generate output

## Day 8

- Informally, a blockchain acts as a database to store information in a specified format and is shared among members of a network with no one entity in control
    - It is a digital database or ledger distributed among nodes of a peer-to-peer network
    - Due to its decentralized nature, each peer is expected to maintain the integrity of the blockchain
- The core blockchain technology aims to be decentralized and maintain integrity; cryptography is employed to negotiate transactions and provide utility to the blockchain
- A majority of practical applications of blockchain rely on a technology known as a smart contract
    - A smart contract is a program stored on a blockchain that runs when pre-determined conditions are met
    - Several languages, such as Solidity, Vyper, and Yul, have been developed to facilitate the creation of contracts
    - Smart contracts can even be developed using traditional programming languages such as Rust and JavaScript; at its core, smart contracts wait for conditions and execute actions, similar to traditional logic
- Most smart contract vulnerabilities arise due to logic issues or poor exception handling

## Day 9

- Docker is a way to package applications, and the associated dependencies into a single unit called an image
    - This image can then be shared and run as a container, either locally as a developer or remotely on a production server
    - A common way to tell if a compromised application is running in a Docker container is to verify the existence of a `/.dockerenv` file at the root directory of the filesystem
- Metasploit is a powerful penetration testing tool for gaining initial access to systems, performing post-exploitation, and pivoting to other applications and systems
    - Metasploit is free, open-source software owned by the US-based cybersecurity firm Rapid7
- After successfully exploiting a remote target with a Metasploit module, a session is often opened by default
    - These sessions are often Command Shells or Meterpreter sessions, which allow for executing commands against the target
    - It’s also possible to open up other session types in Metasploit, such as SSH or WinRM - which do not require payloads
- Meterpreter is an advanced payload that provides interactive access to a compromised system
    - Meterpreter supports running commands on a remote target, including uploading/downloading files and pivoting
- Pivoting: Once an attacker gains initial entry into a system, the compromised machine can be used to send additional web traffic through - allowing previously inaccessible machines to be reached
    - For example, an initial foothold could be gained through a web application running in a docker container or through an exposed port on a Windows machine -- this system will become the attack launchpad for other systems in the network
    - We can route network traffic through this compromised machine to run network scanning tools such as `nmap` or `arp` to find additional machines and services which were previously inaccessible to the pentester - this concept is called network pivoting
- Using Metasploit:
    - In Kali, you can open Metasploit with `msfconsole`
    - Seach/Use a module
    - View/Set options and run the module
        - You can also set options from the `run` command
    - Metasploit has an internal routing table that can be modified with `route`
- Socks Proxy: an intermediate server that supports relaying networking traffic between two machines allowing you to pivot
    - You can run a socks proxy either locally on a pentester's machine via Metasploit or directly on a compromised server
        - In Metasploit, this can be achieved with the `auxiliary/server/socks_proxy` module
    - Tools such as `curl` support sending requests through a socks proxy server via the `-proxy` flag
- If the tool does not natively support an option for using a socks proxy, ProxyChains can intercept the tool’s request to open new network connections and route the request through a socks proxy instead
    - An example with Nmap: `proxychains -q nmap -n -sT -Pn -p 22,80,443,5432 MACHINE_IP`

## Day 10

- Whenever we execute a program, all data will be processed somehow through the computer's RAM (Random Access Memory)
    - If you think of a videogame, your HP, position, movement speed and direction are all stored somewhere in memory and updated as needed as the game goes -- if you can modify the relevant memory positions, you could trick the game into thinking you have more HP than you should or even a higher score
- Cetus is a simple browser plugin that works for Firefox and Chrome, allowing you to explore the memory space of Web Assembly games that run in your browser
    - The main idea behind it is to provide you with the tools to easily find any piece of data stored in memory and modify it if needed
    - It will also let you modify a game's compiled code and alter its behaviors
- Getting certain explicit values from the game (like a riddle answer) will be stored somewhere - a failed attempt and finding out the answer can allow you to search for and bookmark the place in memory of that number
    - This way, the next go round, you can access that answer and bypass that part
- Next, you can start with an EQ search to get all values, trigger a change to a value you want to manipulate, and do a differential search (for increase/decreased values since the first search)
    - Repeated differential searches will narrow down the place in memory of that value (say a health meter) which you can then freeze and/or manipulate as needed

## Day 11

- Memory forensics is the analysis of the volatile memory that is in use when a computer is powered on
    - Computers use dedicated storage devices called Random Access Memory (RAM) to remember what is being performed on the computer at the time
        - RAM is extremely quick and is the preferred method of storing and accessing data
        - This type of data is volatile because it will be deleted when the computer is powered off
        - RAM stores data such as your clipboard or unsaved files
- We can analyze a computer's memory to see what applications (processes), what network connections were being made, and many more useful pieces of information
- A memory dump is a full capture of what was happening on the Computer at the time, for example, network connections or things running in the background
    - Most of the time, malicious code attempts to hide from the user; however, it cannot hide from memory
- A process is a running program; being able to determine what processes were running on the computer will tell us what applications were running at the time of the capture
- On a computer, processes are usually categorized into two groups:
    - User Process: programs that the user has launched (text editors, web browsers, etc)
    - Background Process: programs that are automatically launched and managed by the OS that are typically essential to the OS functioning correctly
- `Volatility` is an open-source memory forensics toolkit written in Python
    - `Volatility` allows us to analyze memory dumps taken from Windows, Linux and Mac OS devices and is an extremely popular tool in memory forensics -- capabilities include;
        - List all processes that were running on the device at the time of the capture
        - List active and closed network connections
        - Use Yara rules to search for indicators of malware
        - Retrieve hashed passwords, clipboard contents, and contents of the command prompt
        - etc
    - Once `Volatility` and its requirements (i.e. Python) are installed, `Volatility` can be run using `python3 vol.py`
    - Flags:
        - `f` points to filepath of memory dump
        - `v` for verbose feedback
        - `p` points to custom plugins location
        - `o` points to filepath of output of extracted processes/DLLs
    - `Volatility` uses plugins to perform analysis, such as:
        - Listing processes
        - Listing network connections
        - Listing contents of the clipboard, notepad, or command prompt

## Day 12

- Malware is software created to harm a computer or an entire network
- Threat actors develop malware to achieve specific goals, such as:
    - Infiltrating networks
    - Breaching sensitive data
    - Disrupting operational services
- Things to look for in Malware include:
    - Network connections: Malware tends to establish either external network connections or internal connections
        - External connections allow remote access or for downloading staged payloads from a threat actors' infrastructure
        - Meanwhile, internal connections allow for lateral movement, a technique used to extend access to other hosts or applications within the network
    - Registry key modifications: Malware typically uses registry keys to establish persistence, a technique used by threat actors to discreetly maintain long-term access to a system despite disruptions
        - A good example is Registry Run Keys, which allows binaries to be automatically executed when a user logs in or the machine boots up
    - File manipulations: Malware also tends to download (one of the common reasons to establish network connections) or create new files needed for its successful execution
- Handling a malware sample is dangerous; some tips for handling live malware:
    - Always assume that malware samples will infect your device; hence executing it is not always the first and only step in analyzing it
    - Only run the malware sample in a controlled environment that prevents potential compromise of unwanted assets
    - It is always recommended to have your sandbox, which allows you have a worry-free execution of malware samples
- A sandbox is a controlled test environment that mimics a legitimate end-user working environment
    - It gives analysts a safe environment to execute malware samples and learn their behavior
- Two ways of analyzing malware:
    - Static Analysis: analysis without execution via profiling the binary
        - Properties
        - Program Flow and Strings
    - Dynamic Analysis: analysis through malware execution in a safe environment
        - Observable behavior and nature of infection
- `ProcMon` (Process Monitor) is a Windows tool that shows real-time registry, file system, and process/thread activity
    - Can exclude certain events (RegOpenKey, RegQueryValue, RegQueryKey, RegCloseKey) to find a backdoor (a process left with both a RegCreateKey and RegSetValue event)
    - Can filter down to file modifications by excluding certain events (CreateFile, CreateFileMapping, QuerySecurityFile, QueryNameInformationFile, QueryBasicInformationFile, CloseFile, ReadFile) to find WriteFile events of note
    - Network activity will show any opened/established connections during the malware run which can yield important information

## Day 13

- Packets are the most basic unit of the network data transferred over the network
    - When a message is sent from one host to another, it is transmitted in small chunks; each called a packet
- Packet analysis is the process of extracting, assessing and identifying network patterns such as connections, shares, commands and other network activities, like logins, and system failures, from the prerecorded traffic files
- Network traffic is a pure and rich data source -- a Packet Capture (PCAP) of network events provides a rich data source for analysis
- Most network-based detection mechanisms and notification systems ingest and parse packet-level information to create alerts and statistical data
- Wireshark is an industry-standard tool for network protocol analysis and is essential in any traffic and packet investigation
    - You can view, save and break down the network traffic with it
    - Use the "Statistics --> Protocol Hierarchy" menu to view the overall usage of the ports and services
    - Close the protocol hierarchy window, use the "Statistics --> Conversations" section and navigate to the IPv4 section to view the list of IP conversations
- RDP (Remote Desktop Protocol) typically runs on port 3389

## Day 14

- Two types of databases:
    - Relationship Databases with tables that relate to one another
    - Non-Relational Databases that do no use tables and store data in documents, graph nodes, or other formats
- Access control is a security element that determines who can access certain information and resources
    - After authentication, access control enforces the appropriate access level
- The OWASP Top 10 list aims to raise awareness regarding common security issues that plague web applications
    - https://owasp.org/Top10/
- IDOR refers to the situation where a user can manipulate the input to bypass authorization due to poor access control
    - IDOR was the fourth on the OWASP Top 10 list in 2013 before it was published under Broken Access Control in 2017

## Day 15

- Several web application vulnerabilities, such as SQL Injection, Cross Site Scripting, and Unrestricted File Upload, stem from the issue of insufficient user input validation
- When poorly handled, file uploads can also open up severe vulnerabilities in the server
    - This can lead to anything from relatively minor nuisance problems; all the way up to full Remote Code Execution (RCE) if an attacker manages to upload and execute a shell. With unrestricted upload access to a server (and the ability to retrieve data at will), an attacker could deface or otherwise alter existing content -- up to and including injecting malicious webpages, which lead to further vulnerabilities such as Cross-Site Scripting (XSS) or Cross-Site Request Forgery (CSRF)
- Unrestricted File Uploads usually have two main exploitation paths:
    - If the attacker can retrieve the uploaded file, it could lead to code execution if the attacker uploads a file such as a web shell
    - If the file is viewed by a user, think of a CV application, then an attacker could embed malware in the uploaded file that would execute on the user's workstation once they view the file
- Protections against Unrestricted File Uploads:
    - File Content Validation: Validate the content of the file by reviewing the ContentType header that is sent by the browser when a file is uploaded
    - File Extension Validation: Validate the file extension -- this will allow us to limit the type of files that can be uploaded
    - File Size Validation: Implement file size validation controls -- this will only allow files sizes smaller than the specified amount
    - File Renaming: Even though uploads are often stored outside the web root, an attacker could leverage an additional vulnerability, such as file inclusion, to execute the file -- To counter these attempts, we can look to rename uploaded files to random names, making it almost impossible for an attacker to recover their file by name
    - Malware Scanning: Scan uploaded files for malware -- we can install a package such as ClamAV and use it to scan the contents of each uploaded file

## Day 16

- Structured Query Language (SQL) is the traditional language used to ask databases for information
- Sanitize inputs and prepare dynamic queries carefully to guard against injection scenarios

## Day 17

- An effective way to validate input is first to know how a specific piece of data is going to be processed by the rest of your application
- Data then goes through syntax and semantic validation checks to ensure that the user-provided values are both proper in their syntax (the answer follows the proper context asked by the question) and logical value (the values make sense for the question
- HTML5’s built-in features help a lot with the validation of user-provided input, minimizing the need to rely on JavaScript for the same objective
    - The `<input>` element, specifically has an array of very helpful capabilities centered around form validation:
        - It can be set to specifically filter for an email, a URL, or even a file, among others, promptly checks whether or not the user-provided input fits the type of data that the form is asking for, and so, feedback on its validity is immediately returned to the user as a result
        - `pattern` attribute also takes regex for more granular control over the validation
- Regex 101:
    - `[a-zA-Z0-9]+` matches any alphanumeric expression
    - `.+@tryhackme\\.com` matches any email that ends with "@tryhackme.com"
    - `[a-z]` matches any lower character in the English alphabet
        - The square brackets indicate that you're trying to match one character within the set of characters inside of them. For example, if we're trying to match any vowel of the English alphabet, we construct our regex as follows: `[aeiou]` -- The order of the characters doesn't matter, and it will match the same
    - You can also mix and match sets of characters within the bracket: `[a-zA-Z]` means you want to match any character from the English alphabet regardless of case
    - Wildcard Operator: `.`
    - The `` operator is used if you don't care if the preceding token matches anything or not, while the`+` operator is used if you want to make sure that it matches at least once
    - To match a string that is alphanumeric and case insensitive, our pattern would be `[a-zA-Z0-9]+`
        - The `+` operator means that we want to match a string, and we don't care how long it is, as long as it's composed of letters and numbers regardless of their case
    - If we want to ensure that the first part of the string is composed of letters and we want it to match regardless if there are numbers thereafter, it would be `^[a-zA-Z]+[0-9]*$`
        - The `^` and `$` operators are called anchors, and denote the start and end of the string we want to match, respectively
    - If we want to match just lowercase letters that are in between 3 and 9 characters in length, our pattern would be `^[a-z]{3,9}$`
    - If we want a string that starts with 3 letters followed by any 3 characters, our pattern would be `^[a-zA-Z]{3}.{3}$`
    - There's also the concept of grouping and escaping, denoted by the `()` and the `\\` operators, respectively
        - Grouping is done to manage the matching of specific parts of the regex better while escaping is used so we can match strings that contain regex operators
    - Finally, there's the `?` operator, which is used to denote that the preceding token is optional
    - If we want to match both [www.tryhackme.com](http://www.tryhackme.com/) and [tryhackme.com](http://tryhackme.com/), our pattern would be `^(www\\.)?tryhackme\\.com$`
        - This pattern would also avoid matching .tryhackme.com
        - `^(www\\.)?`: The `^` operator marks the start of the string, followed by the grouping of www and the escaped `.`, and immediately followed by the question mark operator -- the grouping allowed the question mark operator to work its magic, matching both strings with or without the www. at the beginning
        - `tryhackme\\.com$`: The `$` operator marks the end of the string, preceded by the string tryhackme, an escaped `.`, and the string com
            - If we don't escape the `.` operator, the regex engine will think that we want to match any character between tryhackme and com as well
- free text fields are more free-for-all, and so validations checks are more limited, and the challenge of securing it is generally vaguer -- below are some considerations to ponder on:
    - First, we start again with the question of how this piece of data is going to be processed by the rest of the application
    - What will be the context for which this free-form text field will be used? Free text fields for blog posts are tackled very differently than text fields used for a small comment section or a descriptive text field
    - Is the free text field necessary for your business purposes in the first place, or could it be implemented differently while still achieving the same goal? This is essential to know, too, as part of writing secure code is avoiding writing vulnerable ones
- Implementing both client and server-side validations ensure that no stones are left unturned

## Day 18

- Sigma is an open-source generic signature language developed by Florian Roth & Thomas Patzke to describe log events in a structured format
    - The format involves using a markup language called YAML, a designed syntax that allows for quick sharing of detection methods by security analysts
    - Sigma makes it easy to perform content matching based on collected logs to raise threat alerts for analysts to investigate
        - Log files are usually collected and stored in a database or a Security Information and Event Management (SIEM) solution for further analysis (Sigma is vendor-agnostic; therefore, the rules can be converted to a format that fits the target SIEM)
- YAML:
    - YAML is case-sensitive
    - Files should have the `.yml` extension
    - Spaces are used for indentation and not tabs
    - Comments are attributed using the # character
    - Key-value pairs are denoted using the colon : character
    - Array elements are denoted using the dash - character
- Sigma rules are guided by a given order of required/optional fields and values that create the structure for mapping needed queries

## Day 19

- If we have electricity, how can we generate a digital signal?
    - The approach most hardware components take is to simply turn the power on and off:
        - If the power is on, we are transmitting a digital 1
        - If the power is off, we are transmitting a digital 0
    - We call these 1s and 0s bits where 8 bits make a byte
- We can transmit text data by using the ASCII table (sending the binary representation of each character)
- Some of the most common hardware protocols:
    - USART: Universal Synchronous/Asynchronous Receiver-Transmitter (aka serial communication)
        - Uses 2 wires where one wire is used to transmit (TX) data from device A to device B, and the other wire is used to receive (RX) data on device A from device B
        - There is no clock line that synchronizes communication, so devices must agree on the following config:
            - Communication Speed
            - Bits per Transmission
            - Stop and Start Bits
            - Parity Bits
        - There are a couple of caveats, however:
            - The devices don't really have a way to determine if the other device is ready for communication
                - To solve this, some USART connections will use two additional lines called Clear To Send (CTS) and Request to Send (RTS) to communicate to the other device whether it is ready to receive or ready to transmit
            - Furthermore, to agree upon what voltage level is a binary 1 or 0, a third wire called the Ground (GND) wire is required to allow the devices to have the same voltage reference
    - SPI: Serial Peripheral Interface
        - Mainly used for communication between microprocessors and small peripherals such as a sensor or an SD card
        - SPI uses a separate clock wire
        - Separating the clock (SCK) from the data (DATA) line allows for synchronous communication, which is faster and more reliable
        - The clock line tells the receiving device exactly when it needs to read the data line
            - Two-way communication is also possible, but quite a bit more complex than serial communication
        - Peripheral-In Controller-Out (PICO)
        - Peripheral-Out Controller-In (POCI)
        - While there can only be one controller, there can be multiple secondary devices
            - All devices use the same SCK, PICO, and POCI lines
    - I2C: Inter-Integrated Circuit
        - Created to deal with the drawbacks of both the USART and SPI communication protocols
            - USART is asynchronous and has the clock built into the transmit and receive lines, devices have to agree ahead of time on the configuration of communication -- speeds are reduced to ensure communication remains reliable
            - While SPI is faster and more reliable, it requires many more wires for communication, and every single additional peripheral requires one more Chip Select wire
        - I2C uses a Serial Data (SDA) line and Serial Clock (SCL) line for communication
            - Instead of using a Chip Select wire to determine which peripheral is being communicated to, I2C uses an Address signal that is sent on the SDA wire (this Address tells all controllers and peripherals which device is trying to communicate and to which device it is trying to communicate to)
        - To notify other controllers and peripherals that communication is taking place and prevent these devices from talking over each other, a Start and Stop signal is used
        - Since an external clock line is used, communication is still faster and more reliable than USART, and while it is slightly slower than SPI, the use of the Address signal means up to 1008 devices can be connected to the same two lines and will be able to communicate
- Logic Analyzer: device used to probe the signals being sent on electrical wires between two devices

## Day 20

- Every embedded system, such as cameras, routers, smart watches etc., has pre-installed firmware, which has its own set of instructions running on the hardware's processor
    - It enables the hardware to communicate with other software running on the device
    - The firmware provides low-level control for the designer/developer to make changes at the root level
- Reverse engineering is working your way back through the code to figure out how it was built and what it does
    - Firmware reverse engineering is extracting the original code from the firmware binary file and verifying that the code does not carry out any malicious or unintended functionality like undesired network communication calls
- Firmware Reverse Engineering Process:
    - The firmware is first obtained from the vendor's website or extracted from the device to perform the analysis
    - The obtained/extracted firmware, usually a binary file, is first analyzed to figure out its type (bare metal or OS based)
    - It is verified that the firmware is either encrypted or packed
        - The encrypted firmware is more challenging to analyze as it usually needs a tricky workaround, such as reversing the previous non-encrypted releases of the firmware or performing hardware attacks like Side Channel Attacks (SCA) to fetch the encryption keys
    - Once the encrypted firmware is decrypted, different techniques and tools are used to perform reverse engineering based on type
- Firmware analysis is carried out through two techniques, Static & Dynamic:
    - Static
        - BinWalk: A firmware extraction tool that extracts code snippets inside any binary by searching for signatures against many standard binary file formats like zip, tar, exe, ELF, etc
            - Binwalk has a database of binary header signatures against which the signature match is performed
            - The common objective of using this tool is to extract a file system like `Squashfs`, `yaffs2`, `Cramfs`, `ext*fs`, `jffs2`, etc., which is embedded in the firmware binary
        - Firmware Modkit (FMK): extracts the firmware using binwalk and outputs a directory with the firmware file system
            - Once the code is extracted, a developer can modify desired files and repack the binary file with a single command
        - FirmWalker: Searches through the extracted firmware file system for unique strings and directories like `etc/shadow`, `etc/passwd`, `etc/ssl`, special keywords like `admin`, `root`, `password`, etc., vulnerable binaries like `ssh`, `telnet`, `netcat` etc.
    - Dynamic
        - Qemu: free and open-source emulator and enables working on cross-platform environments
            - provides various ways to emulate binary firmware for different architectures like Advanced RISC Machines (ARM), Microprocessors without Interlocked Pipelined Stages (MIPS), etc., on the host system
            - Qemu can help in full-system emulation or a single binary emulation of ELF (Executable and Linkable Format) files for the Linux system and many different platforms.
        - Gnu Debugger (GDB): a dynamic debugging tool for emulating a binary and inspecting its memory and registers
            - also supports remote debugging, commonly used during firmware reversing when the target binary runs on a separate host and reversing is carried out from a different host

## Day 21

- The Internet of Things (IoT) defines a categorization of just that, “things” -- devices are interconnected and rely heavily on communication to achieve a device’s objectives
    - Examples of IoT include thermostats, web cameras, and smart fridges, to name only a few
- IoT can best be used as a broad categorization of “a device that sends and receives data to communicate with other devices and systems”
- IoT devices tend to be lightweight, which means that the device's functionality and features are limited to only essentials
    - Because of their lightweight nature, modern features may be left out or overlooked, one of the most concerning being security
    - Security is often thought of as secondary, so not ensuring a device can securely communicate with other devices may be a fatal weakness that is overlooked or deemed less important
- An "IoT protocol" categorizes any protocol used by an IoT device for machine-to-machine, machine-to-gateway, or machine-to-cloud communication
    - Should be efficient, reliable, and secure
- 2 Types of IoT Protocols:
    - IoT Data Protocol: relies on the TCP/IP (Transmission Control Protocol/Internet Protocol) model
    - IoT Network Protocol: relies on wireless technology for communication (Wi-Fi, Bluetooth, ZigBee, and Z-Wave)
- An IoT data protocol is akin to common network services you may use or interact with daily, such as HTTP, SMB, FTP, and others (HTTP can be used as the backbone for other IoT protocols or as an IoT data protocol itself)
- Because data communication is the primary objective of IoT data protocols, they commonly take the form of a messaging protocol; that is, the protocol facilities the sending and receiving of a message or payload between two parties
    - Messaging protocols communicate between two devices through an independent server (”middleware”) or by negotiating a communication method amongst themselves
- Popular messaging protocols used by IoT devices:
    - Message Queuing Telemetry Transport (MQTT): A lightweight protocol that relies on a publish/subscribe model to send or receive messages
    - Constrained Application Protocol (CoAP): Translates HTTP communication to a usable communication medium for lightweight devices
    - Advanced Message Queuing Protocol (AMQP): Acts as a transactional protocol to receive, queue, and store messages/payloads between devices
    - Data Distribution Service (DDS): A scalable protocol that relies on a publish/subscribe model to send or receive messages
    - Hypertext Transfer Protocol (HTTP): Used as a communication method from traditional devices to lightweight devices or for large data communication
    - WebSocket: Relies on a client-server model to send data over a TCP connection
- Messaging protocols commonly use a publish/subscribe model, notably the MQTT protocol
    - The model relies on a broker to negotiate "published" messages and "subscription" queries
- A topic is a semi-arbitrary value pre-negotiated by the publisher and subscriber and sent along with a message
    - The format of a topic commonly takes the form of `<name>/<id>/<function>`
    - When a new message is sent with a given topic, the broker will store or overwrite it under the topic and relay it to subscribers who have "subscribed" to it
- Note the asynchronous nature of this communication; the publisher can publish at any time, and the subscriber can subscribe to a topic to see if the broker relaid messages
- Let's consider the default settings of MQTT when it is first deployed. An MQTT broker assigns all devices connected to it read/write access to all topics; that is, any device can publish and subscribe to a topic
    - Following best practices, authentication and authorization should be implemented to prevent potentially bad actors from compromising any principle of the CIA triad
    - Risk is almost solely dependent on the behavior of a device
        - An MQTT instance may be insecure due to improper data regulation best practices
        - An instance may be vulnerable if the device's behavior allows an attacker to perform malicious actions from expected interaction
- Note the differentiation between insecure and vulnerable; an insecure implementation may allow an attacker to exploit a vulnerability, but this does not mean the implementation is inherently vulnerable
- An attacker can discover device behavior from communication sniffing, source code analysis, or documentation:
    - Communication sniffing can determine the protocol used, the middleware or broker address, and the communication behavior
        - For example, unencrypted HTTP requests are sent to a central server, which are then translated to CoAP packets
        - We can observe the HTTP packets and look for topics or message formats that vendors should hide, e.g. settings, commands, etc., to interact with the device
    - Source code analysis can give you direct insight into how a device parses sent data and how it is being used
        - Analysis can identify similar information to communication sniffing but may act as a more reliable and definite source of information
    - Documentation provides you with a clear understanding of the standard functionality of a device or endpoint
        - A disadvantage of only using documentation as a means of identification is that it may leave out sensitive payloads, topics, or other information that is not ordinarily relevant to an end user that we, as attackers want
- Most IoT devices have a device ID that they use to identify themselves to other devices and that other devices can use to identify the target device
    - Devices must exchange this device ID before any other communication can occur
- Once an attacker knows the device ID and behavior of a target device they can attempt to target specific topics or message formats
    - These topics may trust the message source and perform some action blindly (e.g. change a temperature, change a publishing destination, etc)
- 2 libraries for MQTT:
    - Paho: a python library that offers support for all features of MQTT
    - Mosquitto: a suite of MQTT utilities that include a broker and publish/subscribe clients that we can use from the command line

## Day 22

- An attack vector is a tool, technique, or method used to attack a computer system or network -- examples include:
    - Phishing Emails
    - Denial of Service (DoS) or Distributed Denial of Service (DDoS)
    - Web Drive-by Attacks (exploitable flaws in web browsers)
    - Unpatched Vulnerability Exploitation
- The attack surface is the surface area of the victim of an attack that can be impacted by an attack vector and cause damage -- examples include:
    - An email server that is used for sending and receiving emails
    - An internet-facing web server that serves a website to visitors
    - End-user machines that people use to connect to the network
    - Human can be manipulated and tricked into giving control of the network to an attacker through social engineering
- The attack surface cannot be eliminated, but it can be reduced
    - The Greek Phalanx is a good example of a tangible attack surface reduction
    - In cybersecurity, the most secure computer is the one that is shut down and its cables removed
    - Therefore, cybersecurity leaders aim to keep the operations running with the lowest possible attack surface, like creating the digital equivalent of the Greek Phalanx
- Examples of attack surface reduction:
    - Close the ranks
    - Put up the shields
    - Control the flow of information
    - Beware of deception
    - Prepare for countering human error
    - Strengthen every soldier
    - Make the defense invulnerable

## Day 23

- Defense in Depth:
    - Level 1: Perimeter Security
        - Web Application Firewalls (WAFs)
        - Perimeter Network Firewalls
        - Demilitarized Zone (DMZ)
    - Level 2: Defensive Layers
        - Network Segmentation
        - Zero Trust Principle Implementation
        - Least Privileged Access Principle Implementation
        - Hardened Hosts and Networks
    - Level 3: Well-Rounded Defensive Layers
        - Effective Log Collection
        - Well-Crafted Analytics
    - The main difference between levels 2 and 3 is the jiving together of these defensive layers and detection and response mechanisms, allowing for a coherent and well-rounded security posture
