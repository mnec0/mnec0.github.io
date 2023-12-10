# CHAPTER 7 - File & Resource Attacks

## Arbitrary File Upload Vulnerabilities

1. To prevent arbitrary file uploads, **Storing uploaded files in a publicly accessible directory** is NOT a best practice.

2. Developers should follow the security principle of **Assume all user input is malicious and validate rigorously** to prevent arbitrary file upload vulnerabilities.

3. Attackers commonly use the **POST** HTTP method to upload malicious files to a vulnerable server.

4. In the context of arbitrary file upload vulnerabilities, "shell upload" refers to **Uploading files that contain a web shell or malicious code**.

5. A common technique used by attackers to bypass file type restrictions is **Renaming the file to have a different extension**.

6. In the context of bypassing arbitrary file upload filters, "double extension" involves **Appending multiple file extensions to a file name**.

7. Attackers commonly use **Executable files** to exploit arbitrary file upload vulnerabilities.

8. Attackers can potentially bypass PHP version-based file extension filters by **Renaming the file with an allowed extension**.

9. In the context of arbitrary file uploads, "whitelisting" refers to **Permitting only certain file types to be uploaded**.

10. In the context of remote code execution prevention, "sandboxing" refers to **Running code in an isolated environment**.

### **LABORATORY 1**. Vulnerable Apache IV

**Objective**: Your objective is to upload a web shell, execute arbitrary commands on the server and retrieve the flag!

This is the web page interface.

![Alt text](ch7_page_images/image-224.png)

I will create a php shell.

![Alt text](ch7_page_images/image-230.png)

Now I will upload the file.

![Alt text](ch7_page_images/image-227.png)

And now we have command execution.

![Alt text](ch7_page_images/image-231.png)

This is the flag.

![Alt text](ch7_page_images/image-232.png)

### **LABORATORY 2**. Vulnerable Nginx II

**Objective**: Your objective is to upload a web shell, execute arbitrary commands on the server and retrieve the flag!

This is the web page interface.

![Alt text](ch7_page_images/image-233.png)

Let's try the same as before.

![Alt text](ch7_page_images/image-234.png)

When I try to upload a php file we get an error.

![Alt text](ch7_page_images/image-235.png)

Let's try to bypass this.

![Alt text](ch7_page_images/image-239.png)

Upload the file.

![Alt text](ch7_page_images/image-240.png)

And it worked. If we click here we will be redirected to the file.

![Alt text](ch7_page_images/image-238.png)

Now we are in front of an other error.

![Alt text](ch7_page_images/image-241.png)

We just have to append a filename ending with “.php” extension. By doing so, nginx will pass the shell.jpg file to the php handler and the php script will be executed.

![Alt text](ch7_page_images/image-242.png)

And now, find the flag. And show it.

![Alt text](ch7_page_images/image-243.png)
![Alt text](ch7_page_images/image-244.png)


### **LABORATORY 3**. Vulnerable Apache V

**Objective**: Your objective is to upload a web shell, execute arbitrary commands on the server and retrieve the flag!

This is the page interface.

![Alt text](ch7_page_images/image-245.png)

Let's try to upload the php file. Is uploading but is not acting like a php file.

![Alt text](ch7_page_images/image-246.png)
![Alt text](ch7_page_images/image-247.png)

Maybe the page is applying a blacklist. Let's try to bypass this.

![Alt text](ch7_page_images/image-248.png)

![Alt text](ch7_page_images/image-249.png)

And it worked!

![Alt text](ch7_page_images/image-250.png)

Finding the web flag.

![Alt text](ch7_page_images/image-251.png)
![Alt text](ch7_page_images/image-252.png)

### **LABORATORY 4**. WordPress wpStoreCart

**Objective**: Your task is to find and exploit this vulnerability.

This is the web interface. We are in front of a **Wordpress**

![Alt text](ch7_page_images/image-253.png)

Let's use wpscan and try to find some vulnerabilities. It found a plugin.

![Alt text](ch7_page_images/image-254.png)

The url provided by wpscan has directory listing.

![Alt text](ch7_page_images/image-255.png)

Let's search about the plugin. 

![Alt text](ch7_page_images/image-256.png)

This is the exploit. 

![Alt text](ch7_page_images/image-257.png)

It seems that in this path we can upload files and php interprets them.

![Alt text](ch7_page_images/image-260.png)

Uploading the php file with curl.

![Alt text](ch7_page_images/image-259.png)

The file must to be in the uploads directory.

![Alt text](ch7_page_images/image-261.png)

We can inject commands.

![Alt text](ch7_page_images/image-262.png)

## Directory/Path Traversal

1. The HTTP request method commonly used in directory traversal attacks is **GET**.

2. The character(s) typically used to represent directory traversal in a URL is **/**.

3. In a directory traversal attack, the purpose of the "../" sequence is **To escape from the current directory by moving up one level**.

4. The traversal sequence used to access the /etc/passwd file from the /var/www/html/webapp/ directory is **../../../../etc/passwd**.

5. The significance of the "root directory" in the context of directory traversal attacks is **It refers to the top-level directory of a web application**.

6. The PHP function used to move an uploaded file from its temporary location to a permanent location on the server, even if the file extension doesn't match the filter and PHP version, is **move_uploaded_file()**.

7. The name of the parameter that holds the value of the password when logging into OpenEMR is **clearPass**.

8. The file_get_contents function typically returns **A string containing the file's content**.

### **LABORATORY 1**. Directory Traversal

**Objective**: Leverage the directory traversal vulnerability and find more information about the system. 

Select this one.

![Alt text](ch7_page_images/image-263.png)

In this case the content of the directory *documents* is being listed.

![Alt text](ch7_page_images/image-264.png)

Doing a path traversal we can show the content of the */etc*

![Alt text](ch7_page_images/image-265.png)

Select this vulnerability this time.

![Alt text](ch7_page_images/image-266.png)

It is showing the content of the *message.txt* file.

![Alt text](ch7_page_images/image-267.png)

Now try to list the */etc/passwd* doing the path traversal.

![Alt text](ch7_page_images/image-268.png)

### **LABORATORY 2**. OpenEMR Arbitrary File Read (CVE-2018-15140)

**Objective**: Your task is to find and exploit this vulnerability.

Username: admin
Password: password

This is the web page interface.

![Alt text](ch7_page_images/image-269.png)

Let's search about the framework.

![Alt text](ch7_page_images/image-270.png)

Just login with the provided credentials.

![Alt text](ch7_page_images/image-271.png)

Inspecting the exploit we see this, let's try it.

![Alt text](ch7_page_images/image-273.png)

We verify if the path exist, and it does.

![Alt text](ch7_page_images/image-274.png)

Let's open the **Burp Suite** and send the POST request. Transform this.

![Alt text](ch7_page_images/image-278.png)
![Alt text](ch7_page_images/image-280.png)

Into this.

![Alt text](ch7_page_images/image-281.png)

And it works!

![Alt text](ch7_page_images/image-282.png)

## Local File Inclusion (LFI)

1. Developers can prevent LFI vulnerabilities in their web applications by **implementing input validation**.

2. LFI typically falls under the category of **RCE (Remote Code Execution)**.

3. An attacker can escalate an LFI vulnerability into a Remote Code Execution (RCE) vulnerability by **leveraging server-side vulnerabilities to execute code**.

### **LABORATORY 1**. Local File Inclusion

**Objective**: Leverage the Local File Inclusion vulnerability and read system files from the target machine.

Login in the web and select this.

![Alt text](ch7_page_images/image-283.png)

If we select a language and click on **Go** the URL looks like that.

![Alt text](ch7_page_images/image-284.png)

If we insert a file, we can read it.

![Alt text](ch7_page_images/image-285.png)

### **LABORATORY 2**. WordPress IMDb Widget

**Objective**: Your task is to find and exploit this vulnerability.

This is the web page interface and we see is made it with **WordPres**.

![Alt text](ch7_page_images/image-286.png)

Let's launch a **wpscan**. There are a vulnerable plugin.

![Alt text](ch7_page_images/image-287.png)

Let's search about this plugin.

![Alt text](ch7_page_images/image-288.png)

Take a look.

![Alt text](ch7_page_images/image-289.png)

Follow the instructions. And it works, i have the config.php in my attacker pc. Now I have DB credentials. 

![Alt text](ch7_page_images/image-290.png)
![Alt text](ch7_page_images/image-291.png)

Let's try to download the passwd.

![Alt text](ch7_page_images/image-292.png)

## Remote File Inclusion (RFI)

1. In an RFI attack, the primary objective of the attacker is **to execute scripts from a remote source**.

2. "Wrapping" in the context of RFI attacks refers to **a technique for loading code from a remote source**.

3. The HTTP request parameter typically manipulated in an RFI attack to include remote files is **GET Parameters**.

### **LABORATORY 1**. Remote File Inclusion I

**Objective**: Leverage the Remote File Inclusion vulnerability and perform an XSS attack on the web application.

Select this vulnerability

![Alt text](ch7_page_images/image-293.png)

Now for the purpose of taking advantage of the RFI vulnerability we have to have a file that we want to upload (reverse shell). We will find it in this directory.

![Alt text](ch7_page_images/image-294.png)

Copy the *php-reverse-shell.php* in the Desktop and edit it .

![Alt text](ch7_page_images/image-295.png)
![Alt text](ch7_page_images/image-297.png)

Now use netcat for stay listening in the specified port.

![Alt text](ch7_page_images/image-298.png)

And use python to create a server and include the file in the web server.

![Alt text](ch7_page_images/image-299.png)

Now take the remote file (shell.php) from the web. The request has been done.

![Alt text](ch7_page_images/image-300.png)
![Alt text](ch7_page_images/image-301.png)

And we should receive the reverse shell.

![Alt text](ch7_page_images/image-302.png)
![Alt text](ch7_page_images/image-303.png)
