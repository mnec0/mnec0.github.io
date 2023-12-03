# CHAPTER 1 - Introduction to Web Application Security Testing

## Introduction 

1. **Interpretation and Rendering of HTML/CSS:**
   - Web pages are displayed through the interpretation and rendering of HTML/CSS.
   - Responsible Component: *Web Browser*
   - Other options like Database Server, Web Server, and Application Server are not directly responsible for rendering web pages.

2. **Role of JavaScript in Web Development:**
   - Primary Purpose: *Enable Interactivity and Dynamic Content*
   - JavaScript is utilized to make web pages interactive and to handle dynamic content.
   - It is not used for backend data storage, defining page layout, or server-side operations.

3. **Objective of Web Application Security Testing:**
   - **Primary Objective:** Identify and Mitigate Security Vulnerabilities
   - The main goal is to find and address security vulnerabilities rather than exploiting them for unauthorized access.
   - It is not focused on assessing resistance to traffic spikes or simulating user interactions.

4. **Security Testing Involving Vulnerability Exploitation:**
   - **Type of Testing:** *Penetration Testing*
   - Penetration testing involves actively exploiting vulnerabilities to assess their potential impact.
   - Other types like Load Testing, Vulnerability Scanning, and Code Review do not explicitly involve exploitation.

### Common Web Application Threats & Risks

| Threat/Risk | Description |
| ----------- | ----------- |
| Cross-Site Scripting (XSS) | Attackers inject malicious script into web pages viewed by other users, leading to unauthorized access to user data, session hijacking, and browser manipulation. |
| SQL Injection (SQLi) | Attackers manipulate user input to inject malicious SQL code into the application's database, leading to unauthorized data access, data manipulation, or database compomise. |
| Cross-Site Request Forgery (CSRF) | Attackers trick authorized users into unknowingly performing actions on  a web application, such as changing account detail, by exploiting their active sessions. |
| Security Misconfiguration | Improperly confiured servers, databases, or application frameworks can expose sensitive data or provide entry points for attackers. |
| Sensitive Data Exposure | Failure to adequately protect sensitive data, such as passwords or personal information, can lead to data breaches and identity theft. |
| Brute-Force and Credential Stuffing Attacks | Attackers use automated tools to guess usernames and passwords, attempting to gain unathorized access to user accounts. |
| File Upload Vulnerabilities | Insecure file upload mechanisms can enable attackers to upload malicious files, leading to remote code execution or unauthorized access to the server. |
| Denial-of-Service (DoS) and Distributed Denial-of-Service (DDoS) | DoS and DDoS attacks aim to overwhelm web application servers, causing service disruptions and denying legitimate users access. |
| Server-Side Request Forgery (SSRF) | Attackers use SSRF to make requests from the server to internal resources or external networks, potentially leading to data theft or unauthorized access. |
| Inadequate Access Control | Weak access controls may allow unauthorized users to access restricted functionalities or sensitive data. |
| Using Components with Known Vulnerabilites | Integating third-party components with known security flaws can introduce weaknesses into the web application. |
| Broken Access Control | Inadequate access controls can allow unauthorized users to access restricted functionalities or sensitive data. |

1. **Overloading with Excessive Requests:**
   - Type of Threat: **DoS (Denial of Service)**
   - DoS aims to overload the application or server by flooding it with an excessive number of requests.
   - Other options like SQLi, XSS, and CSRF are different types of threats.

2. **Definition of Threat in Cybersecurity:**
   - A threat in cybersecurity refers to an intentional or accidental event that can lead to the exploitation or compromise of a system.

3. **Exploiting Improper Handling of User-Supplied Input:**
   - Type of Threat: **SQLi (SQL Injection)**
   - SQLi targets the application's database by exploiting improper handling of user-supplied input.
   - Other options like CSRF, SSRF, and XSS represent different types of web application threats.

## Web Application Architecture & Components

1. **Purpose of the Back-end:**
   - **Objective:** **To store and manage the application's data and business logic**
   - The back-end handles data storage and business logic, distinct from optimizing performance, executing JavaScript on the client-side, or managing user interface presentation.

2. **Primary Purpose of CSS in Web Development:**
   - **Objective:** **To control the presentation and styling of web pages**
   - CSS is responsible for styling and presentation, not for server-side operations, defining structure, or managing client-side interactivity.

## HTTP/S Protocol Fundamentals

1. **HTTP Version Introducing Persistent Connections:**
   - **Version:** **HTTP/1.1**
   - HTTP/1.1 introduced support for persistent connections, reducing the overhead of establishing new connections for each request.

2. **Data Inclusion in HTTP "POST" Method:**
   - **Location:** **Request Body**
   - When using the HTTP "POST" method, data is included in the request body, not in cookies, headers, or the URL.
  
3. **HTTP Method for Requesting a Resource:**
   - **Method:** **GET**
   - Web browsers use the HTTP "GET" method to request resources from a web server.

4. **Specifying Requested Resource in HTTP Request:**
   - **Part:** **Request URL**
   - In an HTTP request, the requested resource is specified in the request URL, not in status codes, headers, or the request body.

5. **Default Port for HTTP Communication:**
   - **Port:** **80**
   - The default port used by HTTP for communication is 80.

6. **HTTP Header for Caching Response:**
   - **Header:** **Cache-Control**
   - The "Cache-Control" header informs the browser how long it should cache the response.

7. **Content-Type Header in HTTP Response:**
   - **Specifies:** **Type of data in the response body**
   - The "Content-Type" header in HTTP response parsing specifies the type of data in the response body, not size, status code, or character encoding.

8. **Purpose of "Set-Cookie" Header in HTTP Response:**
   - **Purpose:** **Contains data for future requests**
   - The "Set-Cookie" header in an HTTP response contains data needed by the browser for future requests.

9. **Content of "Referer" Header in HTTP Request:**
   - **Contains:** **URL of the previous web page**
   - The "Referer" header typically contains the URL of the previous web page from which the request originated, not user agent, IP address, or request timestamp.

10. **Ensuring Secure Data Transmission in HTTPS:**
   - **Mechanism:** **SSL/TLS encryption during transmission**
   - HTTPS ensures secure data transmission by utilizing SSL/TLS encryption to protect data while it is being transmitted.

11. **Typical Port for HTTPS Communication:**
   - **Port:** **443**
   - HTTPS typically uses port 443 for communication, distinguishing it from other options like 8043, 80, and 8443.

## Testing Lifecycle

### Web App Pentesting Methodology

|  | Phase | Objectives |
| - | ---- | ---------- |
| 1 | Pre-Engagement | ● Define the scope and objective of the penetration test, including the target web application, URLs, and functionalities to be tested.<br>● Obtain proper authorization and permission from the application owner to conduct the test.<br>● Gather relevant information about the application, such as technologies used, user roles, and business-critical functionalities  |
| 2 | Information Gathering & Reconnaissance | ● Perform passive reconnaissance to gather publicly available information about the application and its infrastructure.<br>● Enumerate subdomains, directories, and files to discover hidden or sensitive content.<br>● Use tools like "Nmap" to identify open ports and services running on the web server.<br>● Utilize "Google Dorks" to find indexed information, files, and directories on the target website. |
| 3 | Threat Modeling | ● Analyze the application's architecture and data flow to identify potential threats and attack vectors.<br>● Build an attack surface model to understand how attackers can interact with the application.<br>● Identify potential high-risk areas and prioritize testing efforts accordingly. |
| 4 | Vulnerability Scanning | ● Use automated web vulnerability scanners like "Burp Suite" or "OWASP ZAP" to identify common security flaws.<br>● Verify and validate the scan results manually to eliminate false positives and false negatives. |
| 5 | Manual Testing & Exploiting | ● Perform manual testing to validate and exploit identified vulnerabilities in the application.<br>● Test for input validation issues, authentication bypass, authorization flaws, and business logic vulnerabilities.<br>● Attempt to exploit security flaws to demonstrate their impact and potential risk to the application. |
| 6 | Authentication & Authorization Testing | ● Test the application's authentication mechanisms to identify weaknesses in password policies, session management, and account lockout procedures.<br>● Evaluate the application's access controls to ensure that unauthorized users cannot access sensitive functionalities or data. |
| 7 | Session Management Testing | ● Evaluate the application's session management mechanisms to prevent session fixation, session hijacking, and session-related attacks.<br>● Check for session timeout settings and proper session token handling. |
| 8 | Information Disclosure | ● Review how the application handles sensitive information such as passwords, user data, and confidential files.<br>● Test for information disclosure through error messages, server responses, or improper access controls. |
| 9 | Business Logic Testing | ● Analyze the application's business logic to identify flaws that could lead to unauthorized access or data manipulation.<br>● Test for order-related vulnerabilities, privilege escalation, and other business logic flaws. |
| 10 | Client-Side Testing | ● Evaluate the client-side code (HTML, JavaScript) for potential security vulnerabilities, such as DOM\-based XSS.<br>● Test for insecure client-side storage and sensitive data exposure. |
| 11 | Reporting & Remediation | ● Document and prioritize the identified security vulnerabilities and risks.<br>● Provide a detailed report to developers and stakeholders, including recommendations for remediation.<br>● Assist developers in fixing the identified security issues and retesting the application to ensure that the fixes were successful. |
| 12 | Post-Engagement | ● Conduct a post-engagement meeting to discuss the test results with stakeholders.<br>● Provide security awareness training to the development team to promote secure coding practices. |

1. **Benefits of Following a Penetration Testing Methodology:**
   - **Benefit:** **Ensures consistency and repeatability across different applications**
   - Following a penetration testing methodology ensures a consistent and repeatable testing process, different from limiting scope, saving time, or meeting compliance requirements.

2. **Importance of Structured Web App Pentesting Methodology:**
   - **Importance:** **Provides a systematic approach to identifying and addressing security vulnerabilities**
   - A structured methodology offers a systematic approach to finding and addressing security vulnerabilities, as opposed to guaranteeing accuracy, impressing clients, or focusing on quick completion.

3. **Primary Concern of "Security Misconfiguration" in OWASP Top 10:**
   - **Concern:** **Unauthorized access to sensitive files and directories**
   - Security misconfiguration in OWASP Top 10 primarily relates to unauthorized access to sensitive files and directories, not executing arbitrary commands, mismanaging authentication tokens, or injecting malicious code.

4. **OWASP Top 10 Vulnerability Involving Injection of Malicious Code:**
   - **Vulnerability:** **XSS (Cross-Site Scripting)**
   - XSS involves injecting malicious code into a web application, executed by unsuspecting users, differentiating it from CSRF, SQLi, and IDOR.

5. **OWASP WSTG Section for Identifying Security Misconfigurations:**
   - **Section:** **Configuration Management Testing**
   - Configuration Management Testing in the OWASP WSTG focuses on identifying security misconfigurations in web applications and servers, distinct from input validation, error handling, or authentication testing.

6. **Atypical Activity During Pre-Engagement Phase:**
   - **Activity:** **Requesting the source code for thorough analysis**
   - Requesting the source code of the web application for a thorough analysis is not a typical activity during the pre-engagement phase, unlike identifying scope, gathering security policies, or discussing rules of engagement.

7. **Section of Penetration Test Report Providing Technical Breakdown:**
   - **Section:** **Vulnerability Details**
   - The Vulnerability Details section of the penetration test report focuses on providing a technical breakdown of each identified vulnerability, distinguishing it from methodology, recommendations, and executive summary.

8. **Importance of Including Potential Impact and Risks in the Report:**
   - **Importance:** **To help the organization prioritize remediation efforts based on risks**
   - Including the potential impact and risks in the report helps the organization prioritize remediation efforts based on the risks posed, different from frightening the organization, proving thorough assessment, or justifying costs.
