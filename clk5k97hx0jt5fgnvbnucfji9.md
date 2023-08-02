---
title: "How the Internet actually works. Request-Response cycle"
seoTitle: "How the Internet actually works. Request-Response cycle"
seoDescription: "This purpose of this article is to explain what actually goes on behind the scenes when you type “google.com” into your browser."
datePublished: Tue Jul 11 2023 21:54:23 GMT+0000 (Coordinated Universal Time)
cuid: clk5k97hx0jt5fgnvbnucfji9
slug: how-the-internet-actually-works-request-response-cycle-887a4722694b
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689519442548/f5dfa1f7-9ad9-49c6-9340-77074e38d62d.jpeg
tags: dns, databases, serverless, firewall, load-balancing

---

Research has shown that many Software Engineers struggle with understanding various internet concepts like DNS, TCP/IP and how the internet works in general. This question is a classic and still widely used interview question for many types of software engineering positions. It is used to assess a candidate’s general knowledge of how the web stack works on top of the internet. Taking this article seriously and understanding the request-response cycle means you are already way ahead of the curve.

This purpose of this article is to explain what actually goes on behind the scenes when you type “google.com” into your browser. The following concepts are covered in this post:

* DNS request
    
* TCP/IP
    
* Firewall
    
* HTTPS/SSL
    
* Load-balancer
    
* Web server
    
* Application server
    
* Database
    

### **DNS Requests**

Domain Name System (DNS) is a system that translates domain names to Internet Protocol (IP) addresses. Every computer has an IP address and this address can be used to connect to the computer. An IP address is like a street address; for two computers to communicate, they need to know each other’s address.

Considering the fact that humans remember names better than numbers, we adopted using names to identify computers in addition to IP addresses. So instead of remembering the IP address of every website you want to visit, you can use the website’s domain name.

This is where DNS comes into play. On DNS servers are DNS records containing domain names and their corresponding IP address. So when you type “google.com” into your browser, this queries a DNS server called a DNS rescursor — the server that responds to a DNS query and asks the Authoritative name server (which stores DNS records) for the IP address — and finally return the IP address to your computer and connects you to *google.com*. Note that your computer also stores these DNS records in its cache so it wouldn’t have to go through the whole process again next time you want to visit google.com.

**Vulnerabilities**

It is important to note that DNS caches has its vulnerabilities and they can be manipulated. If your DNS server is manipulated to contain bad DNS records, computers can be deceived into going to potentially harmful websites.

**Access DNS Records**

You can see the DNS record of any domain using the steps below:

· On a Windows computer, open “CMD” app.

· Type *nslookup \[domain name\] e.g nslookup google.com*

You’ll see the DNS record which contains the domain name and IP address of the domain entered.

### **FIREWALL**

If our computer successfully connected to google.com, that means Google’s Firewall system did not consider us as a potential threat and therefore allowed us to connect to its server.

Cisco Systems defines a firewall as a network security device that monitors incoming and outgoing network traffic and decides whether to allow or block specific traffic based on a defined set of security rules.

Firewalls may filter out connections depending on the properties of the connection: source, destination, contents and protocols.

There are different type of firewalls:

· Proxy firewall

· Stateful inspection firewall

· Unified threat management (UTM) firewall

· Next-generation firewall (NGFW)

· Threat-focused NGFW

· Virtual firewall

· Cloud Native Firewall

### **TCP/IP**

After connecting our computer to our host computer (google.com), the two computers need to send data to each other over TCP/IP. Let us talk about what TCP/IP actually is.

TCP/IP (Transmission Control Protocol/Internet Protocol) is a set of communication protocols that enables communication of computers over a network. TCP/IP defines how data is packaged, addressed, transmitted, routed and received over the internet.

Types of TCP/IP protocols include: Hypertext Transfer Protocol (HTTP) — handles communication between a web browser and a web server, Hypertext Transfer Protocol Secure (HTTPS), File Transfer Protocol (FTP) — this enables file transfer between computers.

Before these two computers can send and receive data from each other, they first need to perform what is called a three-way handshake. This process involves our computer sending a packet of data containing a “synchronize” packet and the host computer responding with an “acknowledge” packet and a subsequent “synchronize” packet. Note these packets transferred and received do not contain any actual data.

Once this handshake is complete, the two computers are ready to receive actual data. When both computers are done receiving packets containing data, either computer can close the connection.

### **HTTPS/SSL**

Hyper Text Transfer Protocol Secure (HTTPS) was introduced in 1994 and it has been adopted as the standard for securing an internet connection.

HTTPS is the secure version of HTTP and it encrypts the data sent between a browser and a website. This prevents hackers from stealing information entered on a website.

Google.com makes use of HTTPS in order to secure information entered on its website. This means they installed a valid SSL certificate on their servers.

### **LOAD-BALANCER**

According to Google, google.com processes 100 billion searches every month (which translate to 3.3 billion searches per day and over 38,000 thousand per second). In the light of this fact, it is practically impossible for a single server to process this amount of requests, so google employs the use of multiple servers to process user requests, which in turn improves performance. This brings us to the concept of load balancing.

AWS defines load balancing as the method of distributing network traffic equally across a pool of resources that support an application.

A load balancer is a device that sits between the user and the server group and acts as an invisible facilitator, ensuring that all resource servers are used equally.

When you visit google.com, what you’re met with is a server with a load balancer that sends your request to the next available server, in order to ensure equal distribution of requests throughout their pool of servers.

### **WEB SERVER**

The server to which the load balancer directs your request has a web server software installed on it. This web server is responsible for accepting requests via HTTP or its secure variant HTTPS.

According to Mozilla, a web server is a computer that stores web server software and a website’s component files (for example, HTML documents, images, CSS stylesheets, and JavaScript files).

### **APPLICATION SERVER**

When you make a search request on google.com, the web server accepts the HTTP or HTTPS request and then directs this request to the application server which in turn handles the *business logic* which involves sorting through billions of webpages in its Search index, ranking these search results and finally returning these results to the user. It is the work of the application server to serve dynamic content to the user.

Nginx defines an application server as a server whose fundamental job is to provide its clients with access to what is commonly called *business logic*, which generates dynamic content; that is, its code that transforms data to provide the specialized functionality offered by a business, service, or application.

The application server acts as the middle man between the web server and the code which contains the business logic with which google.com operates.

### DATABASE

When the application server receives the search request from the web server, it extracts the search term which the user inputs and searches its database where these billions of webpages are stored then retrieves them. The database returns the data to the application server which in turn relays the data to the web server and finally returns it to the user.

Wikipedia defines a database as an organized collection of data stored and accessed electronically through the use of a database management system.

The fundamental job of the database is to store the dynamic information you see on google’s search results page.

### **CONCLUSION**

Congratulations. If you read through the article, you now understand how request-response cycle and the internet works in general. You are already way ahead of the curve.

In this article, we covered various concepts including: DNS request, TCP/IP, Firewall, HTTPS/SSL, Load-balancing, Web server, Application server and Database.

Although, the internet is vast with various web technologies coming into light as the day goes by and it might become increasingly difficult to keep up with these technologies, understanding the concepts in this article would go a long way for you as a Software Engineer.

Until next time, keep building.

Follow me on Twitter: [https://twitter.com/DelightGbolahan](https://twitter.com/DelightGbolahan)

And LinkedIn: [https://www.linkedin.com/in/delight-olagbuji](https://www.linkedin.com/in/delight-olagbuji)

### **REFERENCES**

[https://www.varonis.com/blog/what-is-dns](https://www.varonis.com/blog/what-is-dns)

[https://www.cisco.com/c/en/us/products/security/firewalls/what-is-a-firewall.html](https://www.cisco.com/c/en/us/products/security/firewalls/what-is-a-firewall.html)