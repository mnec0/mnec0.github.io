# CHAPTER 9 - CMS Pentesting

## Security Testing Introduction

1. A common vulnerability in Content Management Systems is **CSRF**.

2. Before conducting CMS penetration testing on a website you don't own, you should **seek explicit authorization from the website owner**.

3. In WordPress penetration testing, the term "enumeration" refers to **discovering users, plugins, and themes**.

4. The security testing technique often used to identify vulnerabilities in custom WordPress themes and plugins is **code review**.

5. A common WordPress security best practice that penetration testers may recommend to mitigate vulnerabilities is to **regularly update themes and plugins**.

Certainly! Here are the informative sentences based on the provided questionnaires:

## Information Gathering & Enumeration

1. During a penetration test, the WordPress version can be enumerated by analyzing the website's JavaScript files for version references.

2. The commonly used URL path to access the WordPress README.html file for version enumeration is `/readme.html`.

3. The primary purpose of `xmlrpc.php` in WordPress is to provide an interface for remote communication.

4. Penetration testers can enumerate installed WordPress themes by inspecting the HTML source code for references.

5. The HTTP request method commonly used during file and directory brute forcing is `GET`.

6. When a directory or file is not found on a web server, the typical HTTP response code is `404`.

7. The primary goal of file and directory brute forcing in WordPress security assessments is to uncover sensitive files and directories.

8. The output of the Nmap NSE script `http-wordpress-enum-users` provides a list of users who have commented on the site.

9. The output of the Nmap NSE script `http-wordpress-enum` includes information about the WordPress version and installed plugins.

#### **LABORATORY 1**. WordPress AdRotate

**Objective**: Your task is to find and exploit this vulnerability.

This is the web page interface.

![Alt text](ch9_page_images/image-336.png)

Launch a **wpscan**. It shows a vulnerable plugin. Search about it

![Alt text](ch9_page_images/image-337.png)
![Alt text](ch9_page_images/image-338.png)

Let's read about it.

![Alt text](ch9_page_images/image-339.png)

It exists, can try to do the **SQLi**.

![Alt text](ch9_page_images/image-340.png)

If we use we are displaying the version on the error and in the URL.

![Alt text](ch9_page_images/image-341.png)
![Alt text](ch9_page_images/image-342.png)

#### **LABORATORY 2**. WordPress RCE (CVE-2017-5487)

**Objective**: Your task is to find and exploit this vulnerability.

This is the web page interface.

![Alt text](ch9_page_images/image-343.png)

Let's launch a **wpscan**.

![Alt text](ch9_page_images/image-345.png)

Let's search information about this version and its exploits.

![Alt text](ch9_page_images/image-344.png)

Download it and try. Put the target in the url.

![Alt text](ch9_page_images/image-346.png)

And run it. It works, it displays the id, name, and username.

![Alt text](ch9_page_images/image-347.png)


#### **LABORATORY 3**. WP Security Audit Log plugin Sensitive Information Disclosure (CVE-2018-8719)

**Objective**: Your task is to find and exploit this vulnerability.

This is the web page interface.

![Alt text](ch9_page_images/image-349.png)

Let's launch a **wpscan**.

![Alt text](ch9_page_images/image-350.png)

"/upload" directory has directory listing enabled.

![Alt text](ch9_page_images/image-351.png)

Search about this.

![Alt text](ch9_page_images/image-352.png)

Take a look.

> No protection on the wp-content/uploads/wp-security-audit-log/* which is indexed by google and allows for attackers to possibly find user information.

In the following path we can list a log, getting some information.

![Alt text](ch9_page_images/image-353.png)

After doing some tries in the login page appears a new log file.

![Alt text](ch9_page_images/image-354.png)

Here we have it.

![Alt text](ch9_page_images/image-355.png)

## Vulnerability Scanning

1. In the "vulnerable plugins" section of WPScan's scan output, the information reveals plugins with known vulnerabilities.

2. Files commonly found in the "/wp-content/uploads/" subdirectory of WordPress include Media Files.

#### **LABORATORY 1**. WP Symposium plugin SQL Injection (CVE-2015-6522)

**Objective**: Your mission is to find and exploit this vulnerability.

This is the web page interface.

![Alt text](ch9_page_images/image-356.png)

Launch a **wpscan**. Is showing a plugin. Search about.

![Alt text](ch9_page_images/image-358.png)

The plugin has vulnerabilities.

![Alt text](ch9_page_images/image-359.png)

Take a look.

![Alt text](ch9_page_images/image-360.png)

Try it.

![Alt text](ch9_page_images/image-363.png)
![Alt text](ch9_page_images/image-364.png)

## Authentication Attacks

1. In WordPress security testing, a brute force attack against the WP-JSON authentication endpoint commonly targets the parameter `wp_user` to guess usernames.

2. The HTTP method typically used in a brute force attack against the XML-RPC interface of WordPress is `POST`.

#### **LABORATORY 1**. WordPress Plugin

**Objective**: Your task is to find and exploit this vulnerability.

Username: pentester
Password: password1

They are giving us credentials maybe we can use it to find any vulnerability.

This is the web page interface.

![Alt text](ch9_page_images/image-365.png)

Launch a **wpscan**. Uploads has listing enabled. Nothing interesting, maybe we need to be logged in.

![Alt text](ch9_page_images/image-366.png)

Logging in.

![Alt text](ch9_page_images/image-367.png)

It have a plugin installed. Search information about.

![Alt text](ch9_page_images/image-368.png)
![Alt text](ch9_page_images/image-369.png)

Take a look.

![Alt text](ch9_page_images/image-370.png)

I will recover the shell i have been using since before. Try to upload and execute commands.

![Alt text](ch9_page_images/image-371.png)

Upload the shell.

![Alt text](ch9_page_images/image-373.png)

Now go to the directory and try to inject commands.

![Alt text](ch9_page_images/image-374.png)

We are having command execution.

![Alt text](ch9_page_images/image-375.png)

## Exploiting Vulnerabilities

1. In a WordPress site, file upload filters are typically configured in the `.htaccess` file.

2. To mitigate the risk of arbitrary file upload vulnerabilities in WordPress, web developers and administrators can implement file upload filters.

3. The type of XSS attack that occurs when the malicious script is stored on the target server and served to users who access a specific page or resource is called Stored XSS.

#### **LABORATORY 1**. WP Appointment Booking Calendar Stored XSS (CVE-2020-9371)

**Objective**: Your task is to find and exploit this vulnerability.

```
Username: admin
Password: password1
```

They are giving us credentials maybe we can use it to find any vulnerability.

This is the web page interface.

![Alt text](ch9_page_images/image-376.png)

Launch a **wpscan**. Uploads has listing enabled. Nothing interesting, maybe we need to be logged in.

![Alt text](ch9_page_images/image-377.png)

Logging in.

![Alt text](ch9_page_images/image-378.png)

This are the plugins installed. The uniq active is the "**Appointment Booking Calendar**"

![Alt text](ch9_page_images/image-379.png)

Searching information about. The version match.

![Alt text](ch9_page_images/image-380.png)

Take a look.

![Alt text](ch9_page_images/image-381.png)

Follow the instructions.

![Alt text](ch9_page_images/image-383.png)

And clicking in "Manage Settings" the XSS works.

![Alt text](ch9_page_images/image-384.png)

## WordPress Black-Box Pentest

1. To "double extension" a malicious file during an upload filter bypass attempt means to use two different file extensions in the filename.

2. The file upload filter bypass technique that aims to trick the system into thinking a file is of a different, allowed type is MIME Type spoofing.

### **LABORATORY 1**. Exploiting WordPress

**Objective**: Gain admin access on the WordPress website. Also obtain a shell on the target machine and get the flag file from the target machine.

This is the web page interface.

![Alt text](ch9_page_images/image-385.png)

Launch a **wpscan** and it enumerate a plugin.

![Alt text](ch9_page_images/image-386.png)

Search information about.

![Alt text](ch9_page_images/image-387.png)

We have found a directory with listing enabled and a lot of screenshots inside, we discover a username.

![Alt text](ch9_page_images/image-388.png)

Let's try to log in bruteforcing with **Burp Suite**.

![Alt text](ch9_page_images/image-389.png)

Send it to the **intruder**. Add the payload and start the attack.

![Alt text](ch9_page_images/image-390.png)
![Alt text](ch9_page_images/image-391.png)

Founded.

![Alt text](ch9_page_images/image-392.png)

Now with the credentials and inside the wordpress panel exploit the plugin vulnerability.

Time to follow the exploit instructions and upload the fake image.

![Alt text](ch9_page_images/image-393.png)

Uploading the "image".

![Alt text](ch9_page_images/image-394.png)
![Alt text](ch9_page_images/image-395.png)

Intercept this upload with **Burp Suite**.

![Alt text](ch9_page_images/image-396.png)

Image uploades successfully.

![Alt text](ch9_page_images/image-397.png)

Now start listening with nc and reload the page.

![Alt text](ch9_page_images/image-398.png)
![Alt text](ch9_page_images/image-399.png)

And we get a reverse shell.

![Alt text](ch9_page_images/image-400.png)

Can use commands.

![Alt text](ch9_page_images/image-401.png)

Lets find the flag.

![Alt text](ch9_page_images/image-402.png)

**FLAG**
```bash
2178184f410766ecdda302962a9849a2
```