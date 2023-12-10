# CHAPTER 3 - Web Proxies

## Web Proxies

1. Web proxies can intercept both HTTP and HTTPS traffic.

2. Proxy servers allow you to intercept and modify requests sent between a browser and web application.

## Burp Suite

1. The Burp Suite community edition module with throttling constraints is **Intruder**.

2. In this course, the Burp Suite edition used is **Burp Suite Community**.

3. **Burp Suite Enterprise** provides scalable scanning options.

4. Burp Suite Community Edition does not allow you to filter HTTP history using custom regex.

5. When intercepting requests with Burp Suite, you cannot modify the HTTP headers within a request before forwarding the request to the web app.

6. To send an intercepted request to the web application, you use the **Forward** button.

7. Burp Suite allows you to modify the proxy listener interface and port.

8. In Burp Suite Community edition, you can start a passive crawler limited to a custom scope.

9. The system resource not taken into account when calculating the estimated system impact of a Burp Suite extension is **Disk Space**.

10. The live passive crawler is enabled and active when you first start Burp Suite.

11. Burp Suite allows you to export all links for a specific site in the Site map.

12. The regex expression that would include all subdomains for the domain acme.com when configuring your scope is **.*.acme.com$**.

13. You cannot automate passive crawling in Burp Suite Community edition.

14. When using Burp Suite Community edition, you have the ability to compare Site maps.

15. The Sniper Attack does not utilize more than one set of payloads.

16. The Intruder Attack type that supports the use of multiple payload sets is **Pitchfork**.

17. The Burp Suite Intruder can be used to perform a file and directory brute force attack.

18. When working with the Intruder, you can configure a Payload processing rule to encode the payload in Base64.

19. The Decoder module in Burp Suite does not allow you to decode Base32 strings.

20. The keyboard shortcut used to enable URL encoding as you type in the Repeater is **CTRL + U**.

21. You can utilize the Repeater to view and modify the headers of a request before sending the request.