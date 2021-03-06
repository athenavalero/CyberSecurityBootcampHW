## Unit 18 Homework: Let's go Splunking!

#### Scenario
You have just been hired as an SOC Analyst by Vandalay Industries, an importing and exporting company.

- Vandalay Industries uses Splunk for their security monitoring and have been experiencing a variety of security issues against their online systems over the past few months.

- You are tasked with developing searches, custom reports and alerts to monitor Vandalay's security environment in order to protect them from future attacks.



#### System Requirements
You will be using the Splunk app located in the Ubuntu VM.

#### Your Objective
Utilize your Splunk skills to design a powerful monitoring solution to protect Vandaly from security attacks.
After you complete the assignment you are asked to provide the following:

- Screen shots where indicated.
- Custom report results where indicated.


#### Topics Covered in This Assignment

- Researching and adding new apps
- Installing new apps
- Uploading files
- Splunk searching
- Using fields
- Custom reports
- Custom alerts

Let's get started!


### Vandalay Industries Monitoring Activity Instructions

#### Step 1: The Need for Speed
**Background**: As the worldwide leader of importing and exporting, Vandalay Industries has been the target of many adversaries attempting to disrupt their online business. Recently, Vandaly has been experiencing DDOS attacks against their web servers.

Not only were web servers taken offline by a DDOS attack, but upload and download speed were also significantly impacted after the outage. Your networking team provided results of a network speed run around the time of the latest DDOS attack.

**Task**: Create a report to determine the impact that the DDOS attack had on download and upload speed. Additionally, create an additional field to calculate the ratio of the upload speed to the download speed.


1. Upload the following file of the system speeds around the time of the attack.

    - Speed Test File



2. Using the eval command, create a field called ratio that shows the ratio between the upload and download speeds.

   - Hint: The format for creating a ratio is: | eval new_field_name = 'fieldA'  / 'fieldB'

    ![ratio](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_1.PNG)


3. Create a report using the Splunk's table command to display the following fields in a statistics report:

   - _time
   - IP_ADDRESS
   - DOWNLOAD_MEGABITS
   - UPLOAD_MEGABITS
   - ratio

   Hint: Use the following format when for the table command: | table fieldA  fieldB fieldC

    ![table](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_2.PNG)

4. Answer the following questions:

   - Based on the report created, what is the approximate date and time of the attack?
   
        > Historically, upload speeds are significantly lower than download speeds. From the visualization graphs included in this report, we can see that at approximately 2:30PM on February 23, 2020 to about 11:30PM on the same day, the download speeds were lower than usual and has even almost reached the low levels of upload speeds. From the Speed Test table, we can also see that ratio of download speed against upload speed was at its highest of 0.233 at the same time which seems consistent with our visualization chart. This supports the fact that the attack started at that time. 
        
   - How long did it take your systems to recover?
   
        > Since the download levels seemed to have normalized around 11:30pm, it appears that it took about 9 hours for the systems to recover.

    Submit a screen shot of your report and the answer to the questions above.
    
    ![attack](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_4.png)
    
    ![attack2](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_5_1.png)
    
    
#### Step 2: Are We Vulnerable?

**Background**:  Due to the frequency of attacks, your manager needs to be sure that sensitive customer data on their servers is not vulnerable. Since Vandalay uses Nessus vulnerability scanners, you have pulled the last 24 hours of scans to see if there are any critical vulnerabilities.

  - For more information on Nessus, read the following link: https://www.tenable.com/products/nessus


**Task**: Create a report determining how many critical vulnerabilities exist on the customer data server. Then, build an alert to notify your team if a critical vulnerability reappears on this server.


1. Upload the following file from the Nessus vulnerability scan.

  - Nessus Scan Results



2. Create a report that shows the count of critical vulnerabilities from the customer database server.

  - The database server IP is 10.11.36.23.
  - The field that identifies the level of vulnerabilities is severity.

    ![nessus](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_6.PNG)
    
    ![nessusreport](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_6_2.PNG)
    
    ![nessusreport2](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_6_3.PNG)

3. Build an alert that monitors every day to see if this server has any critical vulnerabilities. If a vulnerability exists, have an alert emailed to soc@vandalay.com.

    Submit a screenshot of your report and a screenshot of proof that the alert has been created.
    
    ![nessusalert](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_7.PNG)
    
    ![nessusalert2](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_8.PNG)
    
    ![nessusalert3](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_9.PNG)

#### Step 3: Drawing the (base)line
**Background**:  A Vandaly server is also experiencing brute force attacks into their administrator account. Management would like you to set up monitoring to notify the SOC team if a brute force attack occurs again.

**Task**: Analyze administrator logs that document a brute force attack. Then, create a baseline of the ordinary amount of administrator bad logins and determine a threshold to indicate if a brute force attack is occurring.


1. Upload the administrator login logs.

  - Admin Logins



2. When did the brute force attack occur?

      > While it appears that at around 8am on February 21, 2020, there is somewhat of a higher count of activity (34 events) than usual (10-23 events), it is not as strong of an indicator of an attack as the 124 events that happened at 9am on the same day. It ended around 1pm also on the same day (123 events), making the attack last for about 4 hours. 

  - Hints:

        - Look for the name field to find failed logins.
        - Note the attack lasted several hours.


    ![bruteforce](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_10.png)

     
        
3. Determine a baseline of normal activity and a threshold that would alert if a brute force attack is occurring.

      > Even though I believe the attack was really prominent at 123-124 events, the higher than usual count of 34 should be enough to trigger an alert especially since the same count was detected around the same time that the brute force attack seems to have ended. This might be an indication that an attack is about to happen so I would set a baseline of 30 to set an alert, giving enough time for the team to look into a possible brute force attack at least an hour before (from this specific event) potential catastrophe from a full-blown brute force attack.

4. Design an alert to check the threshold every hour and email the SOC team at SOC@vandalay.com if triggered.

Submit the answers to the questions about the brute force timing, baseline and threshold. Additionally, provide a screenshot as proof that the alert has been created.

   ![bruteforce2](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_11.PNG)
    
   ![bruteforce3](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_12.PNG)
    
   ![bruteforce4](https://github.com/athenavalero/CyberSecurityBootcampHW/blob/main/Homework%2018/HW18_13.PNG)
    
#### Your Submission
In a word document, provide the following:

  - Answers to all questions where indicated.
  - Screenshots where indicated.
