# CHAPTER 2 - Web Fingerprinting and Enumeration

## Web Enumeration & Information Gathering

### **THINGS TO KEEP IN MIND - Web Enumeration & Information Gathering**
- Website & domain ownership
- IP addresses, domains, and subdomains
- Hidden files & directories
- Hosting infrastructure (web server, CMS, database, etc.)
- Presence of defensive solutions like a web application firewall (WAF)

1. **Port Scanning Technique:**
   - Port scanning is a **False** statement as it is an active reconnaissance technique.

### OWASP Testing Checklist

| ID | WSTG-ID | Test Name | Objectives | Tools | OWASP Top 10 | CWE-IDs | Result | Affected Item | Status |
|----|---------|-----------|------------|-------|--------------|---------|--------|---------------|--------|
| 1.1 | WSTG-INFO-01 | Conduct Search Engine Discovery Reconnaissance for Information Leakage | ● Identify what sensitive design and configuration information of the application, system, or organization is exposed directly (on the organization's website) or indirectly (via third-party services). | Google Hacking Shodan Recon-ng | NA | NA |  |  | Not started |
| 1.2 | WSTG-INFO-02 | Fingerprint Web Server | ● Determine the version and type of a running web server to enable further discovery of any known vulnerabilities. | Wappalyzer Nikto | A5 A6 | CWE-756 CWE-1352 |  |  | Not started |
| 1.3 | WSTG-INFO-03 | Review Webserver Metafiles for Information Leakage | ● Identify hidden or obfuscated paths and functionality through the analysis of metadata files (robots.txt, <META> tag, sitemap.xml) <br> ● Extract and map other information that could lead to a better understanding of the systems at hand. | Browser Curl Burpsuite/ZAP | A1 | CWE-200 |  |  | Not started |
| 1.4 | WSTG-INFO-04 | Enumerate Applications on Webserver | ● Enumerate the applications within the scope that exist on a web server. <br> ● Find applications hosted in the webserver (Virtual hosts/Subdomain), non-standard ports, DNS zone transfers | dnsrecon Nmap | NA | NA |  |  | Not started |
| 1.5 | WSTG-INFO-05 | Review Webpage Content for Information Leakage | ● Review webpage comments, metadata, and redirect bodies to find any information leakage. <br> ● Gather JavaScript files and review the JS code to better understand the application and to find any information leakage. <br> ● Identify if source map files or other front-end debug files exist. | Browser Curl Burpsuite/ZAP | A1 | CWE-200 CWE-540 |  |  | Not started |
| 1.6 | WSTG-INFO-06 | Identify Application Entry Points | ● Identify possible entry and injection points through request and response analysis which covers hidden fields, parameters, methods HTTP header analysis | OWASP ASD Burpsuite/ZAP | NA | NA |  |  | Not started |
| 1.7 | WSTG-INFO-07 | Map Execution Paths Through Application | ● Map the target application and understand the principal workflows. <br> ● Use HTTP(s) Proxy Spider/Crawler feature aligned with application walkthrough | Burpsuite/ZAP | NA | NA |  |  | Not started |
| 1.8 | WSTG-INFO-08 | Fingerprint Web Application Framework | ● Fingerprint the components being used by the web applications. <br> ● Find the type of web application framework/CMS from HTTP headers, Cookies, Source code, Specific files and folders, Error message. | Whatweb Wappalyzer CMSMap | A5 A6 | CWE-756 CWE-1104 |  |  | Not started |
| 1.9 | WSTG-INFO-09 | Fingerprint Web Application | ● N/A, This content has been merged into: WSTG-INFO-08 | NA | NA | NA |  |  | Not started |
| 1.10 | WSTG-INFO-10 | Map Application Architecture | ● Understand the architecture of the application and the technologies in use. <br> ● Identify application architecture whether on Application and Network components: Applicaton: Web server, CMS, PaaS, Serverless, Microservices, Static storage, Third party services/APIs Network and Security: Reverse proxy, IPS, WAF | WAFW00F Nmap | NA | NA |  |  | Not started |

2. **Number of Information Gathering Tests:**
   - OWASP Web Security Testing Guide outlines **10** information gathering tests.

## Finding Ownership & IP Addresses

1. **Whois Lookup for Nameservers:**
   - The Whois lookup utility can be used to identify the nameservers of a particular domain.


2. **Identifying WAF Presence:**
   - Netcraft can be used to identify the presence of a web proxy or web application firewall (WAF).

3. **DNS Record for Resolving Domain to Mail Server:**
   - **MX (Mail Exchange)**
   - MX DNS record is used to resolve a domain to a mail server.

## Reviewing Webserver Metafiles for Information Leakage


1. **Disallow Directive in Robots.txt:**
   - The Disallow directive specifies which resources are prohibited by search engine crawlers.

## Search Engine Discovery

### **Google Dorks**

- `site:namesite`
- `site:namesite key word`
- `site:*.namesite`
- `inurl:forum`
- `intitle:admin`
- `filetype:pdf`

1. **Google Search for Subdomains of INE.com:**
   - `site:*.ine.com`

## Web App Fingerprinting

### **Web App Technology Fingerprinting**

- **Browser Add-ons:** BuiltWith, Wappalyzer
- **Terminal Tools:** whatweb

1. **BuiltWith Browser Add-on for JavaScript Libraries:**
   - The BuiltWith browser add-on can be used to enumerate JavaScript libraries being used on a site.

### **WAF Detection**

- **Tool:** Wafw00f

2. **Enumerating All Possible Instances of a WAF:**
   - **Command:** `wafw00f http://ine.com -a`

## Source Code Analysis

1. **HTTrack Utilizes Spidering:**
   - HTTrack utilizes spidering to find and download files from a webserver.

2. **EyeWitness Downloads Website Source Code:**
   - In addition to taking website screenshots, EyeWitness also downloads the website source code.

## Website Crawling & Spidering

1. **Spidering as a Passive Technique:**
   - Spidering is an active information gathering technique.

## Web Servers

1. **Utilization of robots.txt in http-enum.nse Nmap Script:**
   - The http-enum.nse Nmap script does not utilize the robots.txt file to identify potentially interesting directories.

## DNS Enumeration

### **DNS Zone Transfers**

**DNS RECORDS**
- A
- AAAA
- NS
- MX
- CNAME
- TXT
- HINFO
- SOA
- SRV
- PTR

1. **DNS Record for Domain Aliases:**
   - **CNAME (Canonical Name)**
  
## Subdomains

1. **Sublist3r for Subdomain Enumeration:**
   - Sublist3r can be used to perform brute-force subdomain enumeration.

## Web Server Vulnerability Scanning

1. **Nikto for Identifying Files and Directories:**
   - Nikto can be used to identify potentially interesting files and directories on a web server.

## File & Directory Enumeration

1. **Custom Timeout Duration in Gobuster:**
   - Gobuster provides the ability to specify a custom timeout duration.

## Automated Recon Frameworks

1. **Amass for Resolving Subdomains:**
   - OWASP Amass can resolve subdomains to their respective IP addresses.
