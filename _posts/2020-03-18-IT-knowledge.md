---  
layout: post  
current: post
cover: /cdn.cloudelicious.net/wp-content/uploads/feature_architect-role.jpg
navigation: True
title: IT 관련 잡다한 지식 정리   
tags: technology
class: post-template
subclass: 'post tag-technology'  
author: tigim
---  

Job Interview를 위한 System Architecture 및 Cloud Service에 대한 정리

Technical Part  
===============  

### 웹서비스 or 일반 지식  
- Describe how HTTPS works
- Name five Linux commands that have five or more letters :compress/uncompress, netstat, cksum, hostname, crontab, alias, chown, chmod, touch, whoami, reboot  

- What is a LAMP stack? : Linux operating system, the Apache HTTP Server, the MySQL relational database management system, and the PHP programming language.  

- Describe a web application and all of its components.  

- What is continuous integration? -> (Follow-up 1.) What CI/CD tools have you used? (Follow-up 2.) What are the benefits of CI/CD?

- How does a web server authenticate to a database?
- What is the port for DNS, HTTP, Telnet, etc?
- What is SOAP? What about REST?
- Describe what happens from minute you request for a URL\site, until you get the response back.
- Explain what is DNS? 
- What are some examples of DNS record types?
- How do you stop apache service?

### 네트워크 
- Difference between broadcast, multicast and unicast  
- TCP Model  
- TCP vs UDP -> (Follow-up 1.) Use cases (Follow-up 2.) What newer technologies would use UDP  
- What is the difference between network Layer 2 and 3?  
- Difference between IOPS, Throughput, and Latency
- Describe what happens at Layer 2
- Difference between QOS and bandwidth control
- WAN optimization
- What's a CIDR block and when would you use it?
- What if MPLS? (다중 프로토콜 레이블 스위치)[https://blog.naver.com/yoodh0713/221577551875]
- Is VOIP UDP or TCP? (Answer) mosly UDP, SIP and RTP on UDP are used for VoIP
- Types of load balancers. Load balancer L3 and L5.  
- How does a Load Balancer Work?  
- Which algorithm does an Elastic Load Balancer use? (Answer) hash routing, round robin routing
- router - L3 & switch - L2 & Load Balancer - L4


### 보안 & 해킹   
- Explain difference between asymmetric and symmetric crypto with some use cases (Answer) Encryption algorithms are either symmetric or asymmetric. Symmetric encryption uses the same secret key to perform both the encryption and decryption processes. Asymmetric encryption, also known as public-key encryption, uses two keys, a public key for encryption and a corresponding private key for decryption. The public key and private key are mathematically related so that when the public key is used for encryption, the corresponding private key must be used for decryption. AWS KMS uses only symmetric encryption. 

- What is the difference between an IPSec and an SSL VPN?  
- How would you mitigate a DOS? (Answer) Buffer overflow attacks / Ping of Death or ICMP flood / SYN flood / Teardrop Attack 

- What is identity management?  
- How do you secure a web site?  
- Where are customer encryption keys stored?  
- What's a Web Application Firewall? (Follow-up 1.) How's it differ from a firewall?  
- Stateful and stateless Firewall (Answer) [diffrence between two](https://www.solarwindsmsp.com/blog/stateful-vs-stateless-firewall-differences) 
- What is a Bastion host?: [NAT GW vs Basition Host](http://egloos.zum.com/genes1s/v/3092290)  
- What is DOS/DDOS and how to mitigate this
- What is a web application firewall and how do you use it, what layer is it on?
- How do you secure a web site?
- Explain public/private key encryption 
- What are reasons you would hash a file? 

- IPS/IDS: (Answer 1.) IDS - Intrusion Detection System - very much like a CCTV camera at the entrace. Is a passive system that scans incoming traffic. Once the IDS identifies dangerous/suspicious traffic, it sends alerts to IPS (Answer 2.) IPS - Intrusion Prevention System - actively blocks or prevent intrusions. Once unwelcomed packets are identified, IPS puts them in quarantine or drops them. (Answer 3.) IDS and IPS are not 2 different physical devices. Combined into next generation firewalls.

- What is Federation?(Answer) Federation is a collection of domains that have established trust. The level of trust may vary, but typically includes authentication and almost always includes authorization. A typical federation might include a number of organizations that have established trust for shared access to a set of resources.

- Encryption at rest/in transit (Answer) Password encrypted in DB / HTTPS or SSL

- Asymmetric key encryption was introduced to complement the inherent problem of the need to share the same key in symmetrical encryption model, eliminating the need to share the same key by using a pair of public/private keys.


### 확장성 
- How would you scaling this type of application?  
- What else would you do for a high volume distributed app web site?  
- Discuss durability vs availability 
- Difference between horizontal and vertical scaling (Answer 1.) Horizontal: when you add or remove servers. (Answer 2.) Vertical: When you upscale or downscale a server (i.e. add/remove more CPU or memory)  (Follow-up Q) Why is it hard to horizontally scale a SQL database? 


### 빅데이터 & 데이터베이스 & 스토리지 

- Most common mistakes in DB - [Answer](https://dzone.com/articles/9-of-the-most-common-mistakes-in-database-design)
- In what situations would you want to use a NoSQL database vs. a relational database?  
- Explain how datalake is used for  
- What are the RAID levels (Follow-up 1.) Which one would a DB use? (Follow-up 2.) Is S/W or H/W?
- RAID 10 vs RAID 01 - [RAID 설명](https://blog.naver.com/dilector/221786444049)
- Discuss SSD vs traditional disk 
- What are SQL databases good for?  
- What are NoSQL databases good for?  
- How can a database be scaled?
- What is database indexing and why is it important
- Difference between object storage and file system
- What ports do databases use?
- How would you monitor utilization of equipment in a datacenter
- Different types of storage
- What is a CDN? (Follow-up) How does a CDN make web sites faster (Follow-up) Why is it important who would setup the CDN?
- Why you should use a CDN for a object with a zero TTL? (Answer) a 0 TTL results in a client making an If Modified Since request, hence if the content has not be modified, it will be served from the local cache. If the content has no-cache, it will be fetched everytime regardless of it being expired or not.

- What is difference between cluster and mirroring (Answer 1.) Mirroring, described Mirroring, is the mechanism by which a single database server maintains a copy of a specific dbspace on a separate disk. This mechanism protects the data in mirrored dbspaces against disk failure because the database server automatically updates data on both disks and automatically uses the other disk if one of the dbspaces fails. (Answer 2.) Alternatively, a cluster duplicates on an entirely separate database server all the data that a database server manages, not just the specified dbspaces. Because clustering involves two separate database servers, it protects the data that these database servers manage, not just against disk failures, but against all types of database server failures, including a computer failure or the catastrophic failure of an entire site.

- DAS vs NAS vs SAN  
- Differene between OLTP and DW
- How will you improve the performance of a database? (Answer) add normalization technique.  

- What is Sharding? (Answer) Partition of a huge database into smaller databases in order to gain performance and managebility. Sharding is a method of splitting and storing a larger dataset in multiple databases. Sharding is necessary if a dataset is too large to be stored in a single database. By distributing the data among multiple machines, a cluster of database systems can store larger dataset and handle additional requests.  

- What is De-Duplication in storage? (Answer) Data deduplication is a specialized data compression technique for eliminating duplicate copies of repeating data and reduces storage overhead. Data deduplication techniques ensure that only one unique instance of data is retained on storage media, such as disk, flash or tape. This is also one of the **WAN optimization** techniques

- What is a database caching server?

### 클라우드 기술 & 가상화 

- What is cloud computing? 
- What tools have you used for infrastructure monitoring?  

- What are the top 3 most important aspects of SaaS? (Answer 1.) First, location for clients. Being able to access the software with the least amount of latency is critical. (Answer 2.) Second is security, address PCI, HIPAA, SOC, etc is going to be a concern when clients who maybe competitors use the same software. (Answer 3.) Third is scalability, if you can't handle the growth of new customers and maybe their clients you won't have a product worth scaling and instead increasing the management overhead.

- What is MSA?
- What is "MQTT"?

- What is Virtualization? the basic concepts and terms of virtualization
- What is a Hypervisor and how does it work to distinguish multiple VMs running on it and isolate them from the underlying h/w?
- What is Docker? How does it work?  
- hadoop - explain map-reduce
- hypervisor

### 시스템 디자인 & 최적화   
- Design a HA solution: [참고](https://docs.rightscale.com/cm/designers_guide/cm-designing-and-deploying-high-availability-websites.html)

- Describe how you would build a Content Delivery Network (CDN) from scratch by coding it
- Design fault tolerant, load balanced video stream service  

- Design an e-commerce web page and how would you improve it
- Explain how to scale from a single 5 user database to a 50 user, 500 user, 5000 user and then 5 million user database and explain how to overcome each hurdle.

- Design a hybrid solutions for an enterprise customer that needs to store files online in a private cloud with 99.95% SLA and specify which AWS component you will need to use and details about security, access control etc  (Answer) Tech questions are "easier" but I think a minimum knowledge of AWS and how to architect cloud solutions is required for this role, although I heard a few people saying that no pre knowledge of AWS is required for some roles. Anyway, if you want to work with AWS or be a good professional no matter what provider pls do your homework: signup for a AWS certification courses (a cloud guru, LinuxAcademy, Udemy, edx, LinkedIn Training etc) look at AWS SA blogs, white papers, AWS training and Reinvent on youtube, case studies and examples on LinkedIn presentation and *practice* on the console before trying to pass this interview. 

- If you collected logs and wanted to store them for 14 days then move them over to permanent storage for a few years how would you do this?
- How would you analyze objects stored in S3 and share them with users
- How would a developer make an API friendlier?
- How would you build a web site?
- How do you architect a design that is fault tolerant?
- There is a customer from the relevant domain (for me, it was public sector) that wants to create a site that shows some information, and also, push alerts for the end-users. Expecting Millions of end-users. Describe how to build this application. Consider - security, scalability and availability.   
- How would I optimize a high volume hosted site with slow load times?
- What options are there for database optimization
- Describe how you would architect a very critical website on the cloud? 
- How can you optimize data flow over a high bandwidth/high latency
- Given that you have a content rich E-commerce website, what kind of Storage Tier would you use to support the website?
- How would you recommend to a developer to adjust their code in order to handle database caching?  

### 디버깅 & 트러블 슈팅 

- Troubleshoot a webpage that can't access the DB
- Troubleshoot why you can't access a webpage server
- What's a three tier web page architect,and how do you monitor to see a bottleneck and how do you improve it
- How would you debug a poor-performing data project for an upset client? (Answer 1.) I inquired on what the client was trying to achieve, performed an analysis of the SQL and data schema and recommended corrective actions while explaining the anticipated results. First, you have to define "poor performing". Then perform a full stack assessment: Are instances optimized for their respective roles in the stack? Load balancing in place? Auto-scaling in place? Throughput? Appropriate type of DB (NoSQL vs. RDB), lots of considerations.

- What kind of Metrics would you monitor for the E-commerce website application front-end?
- Case studies for some random startup running on pre y2k technology stack and now wants to scale with AWS. 
- What would you do if a web application could not talk to the database? (Answer 1.) Process of elimination, See if any other apps using the database are down. Try to establish if it's a database server issue. If not I'd move to the firewall and establish port 1521 was open on the database server. If that checked out I would start on the webserver and probably start with rebooting the webserver, since it's down anyway. Start with the simple stuff and work my way through troubleshooting the webserver, is the webserver running, services started, error logs, etc... (Anwer 2.) I would first verify the database is up, check RDS monitoring to see if anything sticks out. Check the security group of the database to ensure that the port the web app connects to it on has the right source sg/subnets (Answer 3.) I will check if there is any firewall and check ports if they are open

- Debug a broken website in the form a CloudFormation stack  

### 소프트웨어 개발 & CI/CD

- How do you write performant Java code?
- What is Big-O notation?
- How java compilation works?
- How JVM compatibility works on various platforms?
- What are the function of stacks? (POP(), PUSH(), TOP())
- How would you identify a circular linked list?
- Difference between bubble sort and merge sort? Given n-million data elements, which would be the best,efficient, and faster sort method? What is the average, best, and worst case performance?
- What is the difference between JSON and XML? When would you use JSON vs. XML?
- What is the difference between scripts (i think he meant command line interpreter) and a compiler?
- What is JSON and why would you use it?
- java & c
- what does kernel do
- Explain the differences between C, C++ and C# 
- OOPS: (Answer) Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which may contain data, in the form of fields, often known as attributes; and code, in the form of procedures, often known as methods. The data is usually hidden from other objects so that the only way to affect the data is through the object’s functions (or methods). It has things like inheritance, abstraction, polymorphism,encapsulation, method overloading/overriding etc..
- Explain inheritance in object oriented programming.
- Write a piece of code to turn a recursive operation into a non recursive one 

- What is continuous integration?
- Machine learning models 


### Summary

- cryptography, data replication, type of raid, cloud concepts, data base and some real scenarios, most common problem in database, virtualization concepts, parallelism, some algorithm, top IP concepts, ports, difference between TCP and UDP

- TCP vs UDP , NAS vs SAN , RAID 5 vs 0+1 , Firewalls , Hypervisor , Load Balancer , Containers, Dockers, Puppet Chef , CDN , Map reducer , big data , SQL vs NO SQL , Router , Switch , OSI model , development tools , unix shell scripting , tuning rdbms , running application , tuning I/O , SOA , Continuous Integration , Continuous deployment , Monolithic application , loosely coupled application , Cloud security, Encryption , dedup, 

- CI and what that means, JSON vs XML, what is a router?  What is MPLS and describe it? How to speed up a high latency link/high speed link? RAID - software vs hardware? What is RAID 10? How to derive IOPS and what are they? What is dedupe? How does it differ from WAN optimizer? I was asked to describe an HA architecture and how to design it. then a series of questions related to RDBMS vs NoSQL, Big Data, and Security.  

- SQL vs NoSQL, Latency, Hyper-V, OOP concepts, CDN's, Containers, Dos and DDos, IPS/IDS, RAID levels, SSD vs Regular Drive  


Customer-Related Part  
=====================  

- How many 9's of availability are required?  (Answer) As many 9's as the customer wants it to be!
- How do you interact with customers?  
- Did you ever come across a customer that his on-premise solution was not going to work in the cloud?
- Tell me about a time you missed a deadline. what happened and what did you learn?  
- What do you tell a client when there is no technical solution ?  
- How do you explain what is cloud to a CEO of a company trying to-move to cloud in less than a minute?  
- How would you scale out a customer experiencing high traffic and slow page responses?
- What if Google decides to host youtube.com on AWS, how do you design your solution?  
- Discuss a situation where you had to convince others.  
- How do you handle security objections about the cloud when dealing with public sector customers?   
- Often times I find I have to take calculated risks, what about you? (Answer) I basically gave an example of how I responsibly made leadership decisions and committed to timelines without having all the information that I needed. 
- You have worked with a lot of cloud projects and products in the XYZ space. You have 45 minutes - impress me.  (Answer) This is an open-ended technical question in which I basically gave a rundown of all the products that I had experience with in the XYZ space and the gotchas as well as knowledge that someone would only know if they had gotten their hands dirty with those products. I had to field a lot of technical questions during my response. They are testing if you can soundly advise a client in that space.  
- worked with change control software
- How you challenge an existing process?  
- How do you sell cloud to a compliance group?

Behaviour Part  
==============  

- Why do you want to work for AWS and why as a Solutions Architect?  
- Describe a time when you disagreed with a management decision and how you expressed your opinion. What were the results?
- Explain an instance of a challenging situation at your current job and what was the resolution?
- Tell me of a time when you had to disagree with your manager because you knew it wasn't the best solution for the customer.  
- Now one of your success and what you learned from it.
- How do you know that you are right?
- Why do you think you will to fit for this job?
- Explain how did you show your leadership skills in absence of your manager  
- What was a difficult situation in the work place and how you handled it?  
- Tell me about a time when you knew you were going to miss a deadline and how you managed it  
- Why a solutions architect?  
- Tell me a situation when you had to assume risks  
- Tell me about a technical engagement you did that you are very proud of.
- Tell me about a time where you disagreed with your manager?  
- What is the biggest mistake you have made?
- Give me a situation where you couldn't solve an issue? nice vague open ended BS question.  
- Explain a time you overcame adversity in school or in the workplace.  
- Example of an experience where I had to make a difficult decision and how I approached the situation.  
- a two-page writing sample on your choice of topics: either something that you've innovated or a risk that you've taken that paid off  
- Of the 14 principles which one do you relate with mostly and use at work, Which one do you not agree with  
- Tell me about a time when you made a judgement call, and you were wrong.  
- What was the last negative feedback you received from your last boss and how did you handle it?  
- biggest achievements...scripting skills..db skills..customer facing skills 
- Describe a moment in your career where you have changed the management decision  
- What is your biggest experience managing projects?  


Specific Area or Cloud Service Related     
=============  
- Describe the business benefits of cloud computing
- What is the significance of 53 in route 53 ?
- Big Data, NoSQL, Database Performance and some Data Modeling etc.
- Why do they call it Amazon Web Services vs. Amazon Web Hosting? 
- How many nodes a SQL 2016 can support
- MS SharePoint Farm topology
- How to host SQL 2015 nodes on AWS
- From your point of view, what are the relevant responsibilities of an AWS Solution Architect?  
- What AWS products have you worked with?
- "do you have an AWS account? what do you do with it?"
- basic terms and components of AWS technology stack
- Questions about managing web application state between EC2 instances running in an auto scaling group
- What is Route 53 and what does the number 53 signify?
- Do you know EMR and Redshift? (Answer)[https://medium.com/@omidvd/when-should-we-use-emr-and-when-should-we-use-redshift-emr-vs-redshift-7328d5a53843]
- how would you encrypt data in a database on AWS (apparently native encryption options in Oracle and MS SQL is a newly supported AWS feature)
- What are the steps involved in migrating customer application from Azure cloud to AWS.  
- Technical discussion on the solution submitted underline assignment (SA) Especially on modern application architecture using microservices and serverless architecture. How does Cognito work with modern architecture? (Anwer) Basically, the intention to cover the internal functionally of Cognito, how the user authenticated and authorised


Tip and Reference  
=================  

- [쿠버네티스 시작전 네트워크 개념/지식 정리](https://blog.naver.com/goduck2)
- I would suggest always preparing about "scalability", "high availability" and security at all tiers. They also concentrated on examples of innovations I had done.  
- [Private Key vs Public Key](https://security.stackexchange.com/questions/9957/can-i-use-a-private-key-as-a-public-key-and-vice-versa)  
- [CORS](https://blog.naver.com/tommybee/221829409848)  
- [NAT 설명](https://blog.naver.com/scw0531/221334568848)  
- [HTTP 에러 코드](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)  
- [CDN, NAS and SAN](https://www.quora.com/What-are-the-differences-between-CDN-NAS-and-SAN)  
- [SOAP vs REST](https://www.slideshare.net/yjaeseok/soap-rest)  
- [An Introduction to HA](https://www.getfilecloud.com/blog/an-introduction-to-high-availability-architecture/)  
- [IOPS vs Throughput](https://stackoverflow.com/questions/15759571/iops-versus-throughput)  
- [MPLS?](https://blog.naver.com/yoodh0713/221577551875)  
- [How CDN speed up a web](https://designshack.net/articles/business-articles/4-ways-a-cdn-can-speed-up-your-website/)  
- [Linux Firewall](https://designshack.net/articles/business-articles/4-ways-a-cdn-can-speed-up-your-website/)  
- [OSI Model](https://nicolaswindpassinger.com/osi-reference-model)  
- [Why JSON better than XML](https://blog.cloud-elements.com/json-better-xml)  
- [Bastion Host](https://terms.naver.com/entry.nhn?docId=816119&cid=42344&categoryId=42344)  
- [NAT gateway vs Bastion Host](http://egloos.zum.com/genes1s/v/3092290)  
- [L4 vs L7](https://jins-dev.tistory.com/entry/L4-L7-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1Load-Balancing-%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)  
- [Load Balancer](https://real-dongsoo7.tistory.com/42)  
- [Amazon 면접 후기](https://caingwiz.tistory.com/29)  
- [HA Design](https://docs.rightscale.com/cm/designers_guide/cm-designing-and-deploying-high-availability-websites.html)  
- [What is docker?](https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html)  
- [Data Structure 101](https://towardsdatascience.com/8-common-data-structures-every-programmer-must-know-171acf6a1a42)

