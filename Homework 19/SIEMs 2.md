## Unit 19 Homework: Protecting VSI from Future Attacks

#### Scenario
In the previous class,  you set up your SOC and monitored attacks from JobeCorp. Now, you will need to design mitigation strategies to protect VSI from future attacks.
You are tasked with using your findings from the Master of SOC activity to answer questions about mitigation strategies.

#### System Requirements
You will be using the Splunk app located in the Ubuntu VM.

#### Logs
Use the same log files you used during the Master of SOC activity:

Windows Logs
Windows Attack Logs
Apache Webserver Logs
Apache Webserver Attack Logs



### Part 1: Windows Server Attack
Note: This is a public-facing windows server that VSI employees access.

#### Question 1

![windowsserver](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2019/HW19_1.PNG)

Several users were impacted during the attack on March 25th.
Based on the attack signatures, what mitigations would you recommend to protect each user account? Provide global mitigations that the whole company can use and individual mitigations that are specific to each user.

  - According to the Windows Server Monitoring Dashboard, the signatures that showed suspicious activity are: user account locked out, attempt made to reset an account’s password, and an account was successfully logged on. One possible solution to mitigate this is by setting up a dedicated VPN to be used by all the users in the company and setting up IP whitelisting. Doing so will ensure that even remote employees would have no issues accessing the server, and ensuring that those attempting to access the server outside of the VPN would not be able to do so. 

#### Question 2

VSI has insider information that JobeCorp attempted to target users by sending "Bad Logins" to lock out every user.
What sort of mitigation could you use to protect against this?

  - To protect the company against Brute Force attacks such as “Bad Logins”, setting up an Account Lockout policy is essential. For example, the user may be locked out after 3 attempts within 5 minutes and unlocking could only be done by a system administrator. To make it stronger, another mitigation strategy could be setting up multi-factor authentication.


### Part 2: Apache Webserver Attack:

#### Question 1

Based on the geographic map, recommend a firewall rule that the networking team should implement.
Provide a "plain english" description of the rule.

For example: "Block all incoming HTTP traffic where the source IP comes from the city of Los Angeles."

  - According to the Apache WebServer Monitoring dashboard, the suspicious activity specifically came from the cities of Kiev (439) and Kharkiv (433) so a potential firewall rule could be: “Block all incoming HTTP traffic where the source IP comes from the cities of Kiev or Kharkiv in Ukraine.”
Provide a screen shot of the geographic map that justifies why you created this rule.

![apache](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2019/HW19_2.PNG)

![apache](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2019/HW19_2.5.PNG)


#### Question 2


VSI has insider information that JobeCorp will launch the same webserver attack but use a different IP each time in order to avoid being stopped by the rule you just created.


What other rules can you create to protect VSI from attacks against your webserver?

Conceive of two more rules in "plain english".
Hint: Look for other fields that indicate the attacker.

  - “Lock accounts that have failed login attempts of more than 3 in a span of 5 minutes.”
  - Since there was a significant count of POST and GET requests (flooding), one way this could be mitigated is by setting up a web application firewall that could identify and track authentic source of traffic. The rule that could be set up would be: “Block all malicious traffic”



### Guidelines for your Submission:
In a word document, provide the following:

Answers for all questions.
Screenshots where indicated

Submit your findings in BootCampSpot!
