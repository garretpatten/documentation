# Getting Started

## Introduction

- When first starting a penetration test or any security evaluation on a target, a primary step is enumeration -- documenting the current state of the target to learn as much as possible about it
- If you're on the same network as a target, you can access it as any user would
  - you can navigate to the IP address of a server running a web page to see what the web page contains
  - you can navigate to the IP address of a storage server and connect to it to explore its files and folders (assuming you have credentials)
- Every server uses ports to serve data to clients, the first step of enumeration is scanning these open ports
  - Services running on ports may be vulnerable
- A tool called `nmap` helps with scanning ports
- Once open ports are found, other tools help you manually access those ports
- 90% of penetration testing consists of research done on the internet about the product you are testing
  - Since it is impossible to know everything in an ever-evolving landscape, you need to know how to look for the information you need -- the ability to research effectively is the skill you need to continuously adapt and evolve into your top quality

## Enumeration

- After a connection is established, ping the target's IP to see if packets reach their destination
- Network Mapper will send requests to the target's ports in hopes of receiving a reply, thus determining if the said port is open or not
  - Some ports are used by default by certain services. Others might be non-standard, which is why we will be using the service detection flag `sV` to determine the name and description of the identified services \*`sudo nmap -sV {target_IP)`
- Following a scan, you can identify ports and what services/protocols they are using
  - Some internet research and you can figure out how to initiate a connection with a service running a specific port of the target
    - This may require username/password authentication, although due to configuration mistakes, some important accounts are left with blank passwords to facilitate accessibility
      - Typical accounts:
        - admin
        - administrator
        - root
    - Scripts can be written to try various username/password combinations for authentication
