<h1>Question 1: Analyse packet1.pcap and find the flag.</h1>
____________________________

<img width="953" height="1013" alt="Screenshot 2026-05-03 210857" src="https://github.com/user-attachments/assets/e8596c3d-83d1-4df8-af48-e0bf70a9a537" />

using (icmp) filter on line 37 the pattern is diferent

<img width="735" height="609" alt="Screenshot 2026-05-03 210916" src="https://github.com/user-attachments/assets/10fa79fb-3161-46c7-9d98-32bae63f7335" />

 we can see a weird string and we can try to use cyberchef

<img width="1905" height="1023" alt="Screenshot 2026-05-03 211642" src="https://github.com/user-attachments/assets/e4a6c8da-576c-424b-9d8a-e0e2a1af7fb8" />

Out of all the base number, only base64 gave us the most logical decode. So i just assume that was the answer

The flag is SUCTF2023{ai_is_cool}

<h1>Question 2: Analyse packet2.pcap and find the flag.</h1>
____________________________
<img width="957" height="1021" alt="Screenshot 2026-05-03 222858" src="https://github.com/user-attachments/assets/011d9f75-2721-4207-9b2f-31290248af35" />

using tcp filter on this line we can see link
<img width="709" height="767" alt="Screenshot 2026-05-03 212436" src="https://github.com/user-attachments/assets/ec862164-045c-44c4-8f3b-e51c77f85a22" />

if we open this link we can see wried symbol

<img width="721" height="108" alt="Screenshot 2026-05-03 212758" src="https://github.com/user-attachments/assets/f5728a40-8af5-4557-99c4-11a646d9e40d" />

<img width="2645" height="1410" alt="image" src="https://github.com/user-attachments/assets/8ed87a58-101d-42d6-9fc4-9f1ac95bfc31" />

i try using some difrent ai and the output is difrent now i do it manualy and the flag is = EXMACHINAAVA

<h1>Question 3: Interpret an Nmap Output</h1>
______________________

|Port    | State | Service      | Version                                  |
---------|-------|--------------|------------------------------------------|
21/tcp  | open   | ftp          | vsftpd 2.3.4
22/tcp  | open   | ssh	         | OpenSSH 5.3p1
80/tcp  | open   | http         | Apache 2.2.8
139/tcp | open   | netbios-ssn  | ddad
445/tcp | open   | microsoft-ds | Windows 7 Professional 7601 Service Pack 1
---------------------------------------------------------------------------

Questions: 
1.	What can an attacker do with each port?
   FTP
  	-	Anonymous login attempts
  	-	Upload/download files

    SSH
  	-	Brute force login
  	-	Credential stuffing

    HTTP
  	-	Web attacj
  	-	Directory navigating

    NetBIOS
  	-	Gather internal network info

    SMB
  	-	Remote Code Execution

   2. What vulnerabilities are likely present based on the version?
      vsftpd 2.3.4
      - Known for backdoor vulnerability (CVE-2011-2523)
     
      OpenSSH 5.3p1
      - Old version. Provide weak encryption, so brute-force is viable

      Apache 2.2.8
      - Outdated, vulnerable to RCE/XSS
     
      Windows 7 Professional 7601 Service Pack 1
      - EternalBlue (MS17-010). Exploitable using metasploit
     
   3. Which one is the highest risk and why?
      FTP
      - Has built-in backdoor
      - No need for brute force or any complex exploit
      - Can gain shell access immediately
     
   4. What attack path can be built from this?
      Common chain from recent lab or tryhackme
      1.    Exploit vsftpd backdoor to gain access (FTP)
      2.	Enumerate system
      3.	Data Extraction or any Hidden content
      4.	Use credential to access SSH
      6.	Escelate privilege
     
   5.  What should be the remediation?
      - Upgrade or remove vsftpd 2.3.4 entirely
      - Patch Windows
 	  - Disable unused ports
	  - Update Apache & SSH
     
    
<h1>Question 4: Identify the OS (OS Fingerprinting) - TTL</h1>
____________________________

*Image 1*
<img width="794" height="278" alt="image" src="https://github.com/user-attachments/assets/717eb5b8-17f1-4210-946f-d24ee4c53ebf" />

Linux

*Image 2*
<img width="440" height="301" alt="image" src="https://github.com/user-attachments/assets/c1dacc11-cbe4-4257-9779-8572ab89f428" />

Networking equipment

*Image 3*
<img width="810" height="186" alt="image" src="https://github.com/user-attachments/assets/1154c373-d3ee-4d5c-acf6-d51ce2dfc255" />

Windows


<h1>Question 5: Analyse the Nessus file</h1>
______________________
<img width="1918" height="976" alt="image" src="https://github.com/user-attachments/assets/1308b6e2-1d66-4494-b090-621deb1b3950" />


1.	What is the affected Port number
   
   <img width="150" height="57" alt="image" src="https://github.com/user-attachments/assets/9e971c15-13d0-421b-aa34-21487939df0e" />

    8009

2.	What is the Affected protocol
   
	TCP AJP protocol

3.	What is the CVSS Score of vulnerability found
	9.8
<img width="377" height="357" alt="image" src="https://github.com/user-attachments/assets/df93cbf2-826f-4ab9-9f38-d3ada02655da" />

4.	Can you find any exploit related to this vulnerability?
<img width="422" height="252" alt="image" src="https://github.com/user-attachments/assets/06107021-cc10-472f-b0f1-2455918d059f" />

5.Find CVE for this vulnerability. 
CVE-2020-1938, CVE-2020-1745
<img width="357" height="138" alt="image" src="https://github.com/user-attachments/assets/8bf5d51d-5e67-4aa6-b170-7f4b4323dc51" />
  

