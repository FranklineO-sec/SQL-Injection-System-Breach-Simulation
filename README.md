# SQL-Injection-System-Breach-Simulation

## Project Overview  
This project was a targeted penetration test against a vulnerable web application to exploit a SQL injection flaw, retrieve sensitive credentials, and gain unauthorized access to a server. The objective was to locate and document a hidden flag file as proof of exploitation. This exercise taught me how an attacker can chain together simple vulnerabilities to compromise an entire system, from a web page to the underlying database and server.  

### Role
Penetration Tester (Capstone Simulation)

### Skills Learned  
- SQL injection exploitation techniques.  
- Extracting and cracking credential hashes.  
- Authentication bypass simulation.  
- Applying secure coding practices.  

### Tools Used  
- **DVWA** – Vulnerable web application.  
- **SQLMap** – Automated SQL injection exploitation.  
- **CrackStation** – Password cracking.  
- **Web Browser** – Manual SQL injection testing.  

## Methodology   
1. I began by logging into DVWA and setting the security to a low level for testing.  
2. Next, I used SQLMap, a powerful tool for automating the discovery and exploitation of SQL injection flaws. I executed the following command to enumerate database tables and extract data: `sqlmap -u "http://<target_ip>/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit" --dbs --tables -D dvwa`  
3. Upon successfully extracting usernames and their associated password hashes from the users table, I used an online cracking tool, CrackStation, to crack the MD5 hash for "Bob Smith".  
4. With the plaintext password in hand, I logged in via SSH with the cracked credentials, gaining unauthorized shell access to the server.
5. Finally, I navigated the file system and retrieved the challenge flag.

## Key Findings
​- The database was vulnerable to unauthenticated SQL injection.  
​- The application used weak password hashes (MD5 with no salting).  
​- The server allowed remote SSH login with the compromised credentials. 
 
## ​Remediation Recommendations
​- Replace dynamic queries with prepared statements to prevent SQL injection.  
​- Validate and sanitize all user inputs.  
​- Restrict database permissions to only essential operations.  

## ​Personal Reflection
​This project was a fantastic demonstration of the "exploit chain." It taught me a valuable lesson that even a seemingly simple vulnerability like SQL injection can have a catastrophic impact when chained with other weaknesses. It highlighted the importance of robust input validation and secure coding practices from the start.
 

*Ref 1: SQLMap hash extraction output*  

<img width="1050" height="590" alt="image" src="https://github.com/user-attachments/assets/a6fdd077-d3a6-4821-8e7b-faeddc1ab3c5" />

*Ref 2: Cracked password access confirmation*  

<img width="1050" height="557" alt="image" src="https://github.com/user-attachments/assets/052ebf3f-8b4a-4573-bcc7-5485e79b1e47" />
<img width="1050" height="590" alt="image" src="https://github.com/user-attachments/assets/1dddc52c-eed9-4a9c-aa66-c14d3926dd09" />
<img width="1050" height="590" alt="image" src="https://github.com/user-attachments/assets/0220350e-6bdf-4698-8984-daa6dd1a1473" />
<img width="1050" height="129" alt="image" src="https://github.com/user-attachments/assets/2773a731-aed0-4685-8d2d-240edb1f2719" />



