# Step 1) Information Gathering

Information gathering is the first step for any penetration test. It involves gathering or collecting information about a target individual, company, website, or system.

"The more information, the better."

## Passive Information Gathering
Involves gathering as much information as possible **WITHOUT** actively engaging with the target.

### Typical information to identify:
1. IP addresses & DNS information
2. Domain names and ownership information
3. Email Addresses and social media profiles
4. Web technologies
5. Subdomains


### Non-Bash Techniques:
- /robots.txt
- /sitemaps.txt
- builtwith - firefox extension shows website tech stack
- netcraft.com - aggregates lots of information from target
- dnsdumpster.com - find and lookup dns records
- googledork
- waybackmachine.com
- haveibeenpwned.com - indentify emails involved in data breaches

### Bash Commands:
#### Find IP address from Domain Name
```bash
host {website}
```

#### Find Website Technology Stack
```bash
whatweb {website}
```

#### Find Domain Information
```bash
whois {website}
```

#### Check NS Recprds for Zone Transfers
```bash
dnsrecon -d {website}
```

#### Check for Web Application Firewalls (WAF)
```bash
wafw00f {website}
```

#### Passively Enumerating Subdomains
```bash
python sublist3r.py -d {website} -e {engine1,engine2...}
```

#### Identify emails associated with target
```bash
theHarvester -d hackersploit.org -b duckduckgo,yahoo,...
```

## Active Information Gathering
Involves gathering as much information as possible by actively engaging with the target system.

### Typical information to look out for:
1. Discovering open ports
2. Learning about target's internal infastructure
3. Enumerating information from target systems

#### Active DNS Interrogation - Enumerating DNS Recods
```bash
dnsenum {website}
```

```bash
fierce -dns {website}
```

### Nmap
This sub-section for active information gathering dedicated to nmap because it is a very versatile, handy tool.

***!!! Important: Nmap is typically used once connected to target's network !!!***

#### Host Discovery
```bash
nmap -sn 127.0.0.1/24
```
- *"-sn": no port scan*
- *24 is the subnet which can be found using "if a s"*

#### Port Scanning
```bash
nmap -Pn {ip}
```
- "-Pn": used for window systems
- "-sU": udp port scan
- "-F": Top 100 common ports (default 1000)
- "-p{port range or num}": ie) -p- -p50-100 -p50
- "-sV": to find service versions
- "T{0-5}": speed of scan + stealth