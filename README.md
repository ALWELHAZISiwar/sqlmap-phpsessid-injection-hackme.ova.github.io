
# 🛡️ SQL Injection with SQLMAP Using PHPSESSID Cookie  

## Project Description  
This project demonstrates how to perform a SQL injection attack using the SQLMAP tool with a PHPSESSID cookie for authentication. This exercise showcases techniques for discovering vulnerabilities in web applications, leveraging tools like 🔍 Nmap, 🌐 Dirbuster, and 🛠️ SQLMAP.  

⚠️ **This project is strictly for ethical purposes, conducted in a controlled environment, and should only be replicated with permission.**  

---

## 🖥️ Prerequisites  
- **🐧 Kali Linux VM**: Used as the attack machine.  
- **🏴 Hackme: 1 VM**: The vulnerable target machine (`hackme.ova`).
- Link of hackme.ova: https://www.vulnhub.com/entry/hackme-1,330/
-  i used VMWARE. 

---

## ⚙️ Steps Performed  

### 1. 🔍 Discover the Target's IP Address  
Use Nmap to scan the network and identify the IP address of the target VM.  

```bash  
nmap -p- -A <target-ip>  
```  
- Ensure that the target machine is accessible and port 80 is open.  

### 2. 🌐 Web Directory Enumeration  
Run Dirbuster (set to medium intensity) to discover directories and files on the web server.  
-link:https://raw.githubusercontent.com/daviddias/node-dirbuster/refs/heads/master/lists/directory-list-2.3-medium.txt
```  
Dirbuster > Input Target IP > Medium Scan  
```  

### 3. 🛠️ Account Creation and Login  
- Navigate to the web application on the target machine.  
- Create a new user account and log in.  

### 4. 🧩 Extracting the PHPSESSID Cookie  
Inspect the network traffic on the **welcome page** (e.g., using browser developer tools).  
- Identify and extract the `PHPSESSID` value from the cookies.  

### 5. 💉 SQL Injection with SQLMAP  
Use SQLMAP to perform SQL injection on the target application's URL, passing the `PHPSESSID` cookie for authentication.  

```bash  
sqlmap -u http://<target-ip>/welcome.php --cookie "PHPSESSID=<session-id>" --forms --dbs  
```  
- Replace `<target-ip>` with the discovered IP address of the target.  
- Replace `<session-id>` with the extracted PHPSESSID value.  

### 6. 🗂️ Database Enumeration  
Once SQLMAP identifies the vulnerability, enumerate the databases using the `--dbs` option.  

---

## 📊 Results  
By following the steps above, SQLMAP successfully identifies and exploits a SQL injection vulnerability in the web application. The database structure is enumerated, demonstrating how attackers can leverage insecure coding practices to compromise systems.  

---

## 🤝 Ethical Considerations  
This project was conducted in a controlled lab environment and is intended solely for educational purposes.  
✅ **Only perform such activities on systems you own or have explicit permission to test.**  
❌ **Unauthorized use of these techniques is illegal and unethical.**  

---

## ⚠️ Disclaimer  
The information provided here is for educational and ethical hacking purposes only. The author assumes no responsibility for misuse or illegal activities conducted using this information. Always follow applicable laws and ethical guidelines.  

---

### ✍️ Created by  
**Siwar ALWELHAZI**  
💻 Cybersecurity Engineer  
``` 
