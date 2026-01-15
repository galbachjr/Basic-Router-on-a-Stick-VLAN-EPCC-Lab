<h1>"Basic Router-on-a-Stick VLAN EPCC Lab</h1>

<h2>Description</h2>
My first HackTheBox Sherlock lab write-up, investigating an SSH brute-force attack by analyzing Linux authentication logs using Ubuntu (WSL).
<br />


<h2>Prerequisites</h2>

- <b>HackTheBox Lab</b> 
- <b>Linux Terminal / Windows WSL Linux Ubuntu Terminal</b>
- <b>Brutus Folder</b>
- <b>7zip</b>

<h2>Objectives</h2>

- <b>Analyze Linux authentication artifacts (auth.log and wtmp) to identify evidence of an SSH brute-force attack.</b>
- <b>Trace attacker activity post-compromise, including successful logins, privilege escalation, and persistence indicators.</b>
- <b>Practice basic incident investigation using Linux command-line tools within an Ubuntu (WSL) environment.</b>

<h2>Step 1: Setting Up The "Brutus" Lab</h2>

<p align="center">
1) Downloading The Brutus.zip File Onto Desktop & Utilizing 7zip to Extract to "Brutus\". <br/>
<img src="https://i.imgur.com/B8Nc55l.png" height="80%" width="80%" alt="#1"/>
<br />
<br />
2) Entering the password given for the Brutus.zip File "hacktheblue".  <br/>
<img src="https://i.imgur.com/qoiWqLQ.png" height="80%" width="80%" alt="#2"/>
<br />
<br />
3) Downloading WSL & Installing a Linux Distrubition (I Used Ubuntu)  <br/>
<img src="https://i.imgur.com/tTILjoh.png" height="80%" width="80%" alt="#3"/>
<br />
<br />
4) Opening the Brutus Folder with the Linux Shell you Downloaded.  <br/>
<img src="https://i.imgur.com/0FtBLzQ.png" height="80%" width="80%" alt="#4"/>
<br />


________________________________________________________________________________________________________
<h2>Step 2: Investigating The Brutus auth.log File.</h2>

 <p align="center">
1) Since this scenario is of a bruteforce attack, I will use some keywords such as "accepted" , "failed" , and "failed password" using the grep command to filter through the auth.log and see information regarding the successful/unsuccessful attempts of logging into the compromised server which its ip is 172.31.35.28. <br/> 
<img src="https://i.imgur.com/RXVvWJO.png" height="80%" width="80%" alt="#5"/>
<br />
<img src="https://i.imgur.com/VPUedwC.png" height="80%" width="80%" alt="#6"/>
<br />
<img src="https://i.imgur.com/L4zeTqT.png" height="80%" width="80%" alt="#7"/>
<br />
2) From looking at this image, I had saw a lot of logins from a another account and to the root (admin) account from a wierd IP address, so I had decided to use the curl command with the wepsite ipinfo.io to search the details of this IP to find any suspicious information.
<br />

________________________________________________________________________________________________________
<h2>Step 3: Investigating The Login Attempts From A Suspicious IP Address.</h2>

<p align="center">
Checking The Successful Logins From The 65.2.161.68 IP Address:  <br/>
<img src="https://i.imgur.com/ZFEvWvn.png" height="80%" width="80%" alt="#8"/>
<br />

<p align="center">
Looking At Logs Regarding The Root Account:  <br/>
- <b>I had used the grep command with the keyword "root" to see all the logs pertaining to the root user and had saw a successful session for the root user which had came from the suspicious IP address 65.2.161.68.</b>
<br />
<img src="https://i.imgur.com/TjvlaSj.png" height="80%" width="80%" alt="#9"/>
<br />
________________________________________________________________________________________________________
<h2>Step 4: Investigating The Suspicious User "cyberjunkie"</h2>

<p align="center">
Suspicious Sudo Session Created By cyberjunkie:  <br/>
- <b>After looking at few more logs, I had came across a suspicious sudo session created by an unknown user named "cyberjunkie" which had downloaded a script to the server and questioned how did this user be able to run the "sudo" command?</b><br/>
<img src="https://i.imgur.com/v2wBSRY.png" height="80%" width="80%" alt="#10"/>
<br />

 <p align="center">
Investigating All Logs Regarding cyberjunkie: <br/>
- <b>After finding this suspicious user "cyberjunkie", I had utilized the grep command with the keyword "cyberjunkie" to see all commands that were linked with this user and had saw the attacker add one of the backdoor accounts he placed to the sudo group and was linked to the same suspicious IP address 65.2.161.68.</b>
<img src="https://i.imgur.com/bJK6ESq.png" height="80%" width="80%" alt="#11"/>
<br />
________________________________________________________________________________________________________
<h2>Step 5: Answering The Rest Of The Answers In HackTheBox</h2>

<p align="center">
Identifying The First Timestamp That The Attacker Logged Into The Server:  <br/>
- <b>Since the timestamps were found in the wtmp artifact and using the "cat" command would make the text unreadable, I had used the "utmpdump" command to view the contents of the file in a human-readable raw text form.</b>
<img src="https://i.imgur.com/42HwpBw.png" height="80%" width="80%" alt="#12"/>
<br />

<p align="center">
Identifying The SSH Login Assigned To The Attacker's Session:  <br/>
- <b>I had utilized the "grep" command again with the two key words "session" and "root" to see all sessions made to the root user, and had saw the SSH Login Session 37 matching the same timestamp March 6 06:32:44 from when the attacker first logged into the server.</b>
<img src="https://i.imgur.com/RAkv3RP.png" height="80%" width="80%" alt="#13"/>
<br />

<p align="center">
Determining the MITRE ATT&CK sub-technique ID used for persistence by creating a new account:  <br/>
- <b>Using the https://attack.mitre.org/ website, I had searched up "Create Account: Local Account" and had found the sub-technique ID used for this attack to be T1136.001.</b>
<img src="https://i.imgur.com/DOMGc4x.png" height="80%" width="80%" alt="#14"/>
<br />

<p align="center">
Identifying The End Of The Attacker's First SSH Session:  <br/>
- <b>Looking at the same timestamp from the Attacker's first session, we can see that it had ended a few minutes after which was on March 6 06:37:24</b><br />
<img src="https://i.imgur.com/McuTf7A.png" height="80%" width="80%" alt="#15"/>
<br />
________________________________________________________________________________________________________
<h2>OVERVIEW:</h2>
<p align="center">
Sherlock Brutus Completion:  <br/>
<p align="left">
<b> 1) Completed my first Hack The Box Sherlock lab focused on investigating an SSH brute-force attack.</b>
<p align="left">
<b> 2) Brushed up on core Linux command-line skills and learned new commands such as utmpdump to convert system login logs into human-readable text.</b>
<p align="left">
<b> 3) Set up WSL with Ubuntu on a Windows 11 laptop, allowing Linux-based analysis without using a virtual machine.</b>
<p align="left">
<b> 4) Gained hands-on experience analyzing authentication logs (auth.log, wtmp) and filtering logs to identify suspicious activity.</b>
<p align="center">
<img src="https://i.imgur.com/nminqwp.png" height="80%" width="80%" alt="#16"/>
<br />


- https://github.com/galbachjr
________________________________________________________________________________________________________
  

</p>
