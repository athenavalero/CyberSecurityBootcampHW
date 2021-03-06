## Week 16 Homework Submission File: Penetration Testing 1

#### Step 1: Google Dorking
- Using Google, can you identify who the Chief Executive Officer of Altoro Mutual is:

  > Karl Fitzgerald
- How can this information be helpful to an attacker:

  > This is information that can be used to perform social engineering or phishing.



#### Step 2: DNS and Domain Discovery
Enter the IP address for demo.testfire.net into Domain Dossier and answer the following questions based on the results:

  ![Domain Dossier](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_1.PNG)
  
1. Where is the company located:
 
   > Sunnyvale, CA
   
   ![Location](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_2.PNG)


2. What is the NetRange IP address:

   > 65.61.137.64 - 65.61.137.127

   ![Netrange IP](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_3.PNG)

3. What is the company they use to store their infrastructure: 

   > Rackspace Backbone Engineering (C05762718)
 
    ![Company](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_3.PNG)  

4. What is the IP address of the DNS server: 

   > 65.61.137.117

    ![DNS Server IP](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_1.PNG)

#### Step 3: Shodan

- What open ports and running services did Shodan find:

  > - Open Ports: 80, 443, 8080
  > - Services: Apache Tomcat/Coyote JSP Engine (1.1)

 ![Shodan](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_9.PNG)

#### Step 4: Recon-ng

- Install the Recon module xssed.
 
  > marketplace install xssed

  ![Install xssed](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_5.PNG)

- Set the source to demo.testfire.net.

  > options set SOURCE demo.testfire.net
  
  ![Set source](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_5.PNG)
  
- Run the module.

  > run

  ![Run module](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_6.PNG)

Is Altoro Mutual vulnerable to XSS: 

   > Yes. Per the screenshot provided, there is a vulnerability to XSS found.
   
   ![Run module](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_6.PNG)

#### Step 5: Zenmap
Your client has asked that you help identify any vulnerabilities with their file-sharing server. Using the Metasploitable machine to act as your client's server, complete the following:


- Command for Zenmap to run a service scan against the Metasploitable machine:

  > nmap-T4-A-v 192.168.0.10

- Bonus command to output results into a new text file named zenmapscan.txt:
 
  

- Use Zenmap's scripting engine to identify a vulnerability associated with the service running on the 139/445 port from your previous scan. Zenmap vulnerability script command:
 
  > nmap--script ftp-vsftpd-backdoor 192.168.0.10

   ![139/445](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2016/HW16_8.PNG)


- Once you have identified this vulnerability, answer the following questions for your client:


 1. What is the vulnerability:
 
     > SMB Listening in on Port


 2. Why is it dangerous:
 
    > Since ports 139 and 445 are SMB ports, these ports being open can be vulnerable to exploit by port listening. 

 3. What mitigation strategies can you recommendations for the client to protect their server:
  
    > - Ensure that systems are up-to-date
    > - Use Firewall or VPN
    > - Make sure that there is redundancy (back-up of files) in case of attack
   
