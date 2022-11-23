# Honeypot Assignment

**Time spent:** **15** hours spent in total

**Objective:** Create a honeynet using MHN-Admin. Present your findings as if you were requested to give a brief report of the current state of Internet security. Assume that your audience is a current employer who is questioning why the company should allocate anymore resources to the IT security team.

## MHN-Admin Deployment (Required)

- [x] **Summary:**
* I deployed MHN-Admin in Kali by creating VM instances & using Google Cloud Platform (GCP) with the following honeypots: Dionaea, Snort & p0f.
* At first I created a google cloud account and then created a project.
* Then I initialized gcloud in the kali terminal and computed specific firewall rules to allow HTTP traffic and all ports from anywhere.
* Then I created the mhn-admin VM, took a note of the external IP address and established SSH access to the VM.
* After establishing SSH access, I installed MHN through the mhn-Admin VM and chose a super user email & password.
* Finally I was able to load the external IP in a browser and login to the MHN admin console via the "superuser" values. I was also able to see the mhn-admin VM instances status through the google cloud web console.

- [x] **GIF Walkthrough:**
<img src="mhn-admin.gif">

## Dionaea Honeypot Deployment (Required)

- [x] **Summary:** 
* First I created the firewall rule to allow incoming TCP and UDP traffic on all ports for honeypot sensors, created the VM for dionaea honeypot called honeypot-1 make note of the external IP and established SSH access to the VM where I executed the deploy command for dionaea that I copied from the MHN admin console.
* Now that the dionaea honeypot is listed in the sensor, I performed an attack using nmap, passing it the external IP of the dionaea honeypot VM. As a result multiple ports were opened which Dionaea was using to attract attackers.
* After the attack in the Attacks page of the MHN Admin console, I was able to see my IP address listed with several port scan records which is the evidence that the honeypot intercepted my attack.
* Attacks from other IPs were also coming in at an alarming rate, from all over the world.
* The most often attacked honeypot was dionaea. This is likely due to a wider attack surface.
* No payload or signatures samples were collected by this sensor.
* Dionaea is able to trap malware exploiting vulnerabilities exposed by services offered to the
network. The main goal of Dionaea honeypot deployment is gaining a copy of malware which can be a known or an unknown malware attack.

- [x] **GIF Walkthrough:**
<img src="dionaea-honeypot.gif">

## Database Backup (Required) 

- [x] **Summary:**
* MHN-Admin uses the MongoDB relational database management system for logging events. 
* From the JSON file record we can get the unique identifier, protocol, the timestamp of the connection, the source IP, the source and destination ports, and what honeypot was scanned.
* [session.json](https://github.com/sanjanabintaazad/codepath_homework/blob/Honeypot/session.json)

## Deploying Additional Honeypot(s) (Optional)

### 1. Snort Honeypot

- [x] **Summary:**
* Snort is an open source intrusion prevention system capable of real-time traffic analysis and packet logging.
* To deploy snort honeypot, first I created the VM for snort honeypot called honeypot-2 make note of the external IP and established SSH access to the VM where I executed the deploy command for snort that I copied from the MHN admin console.
* Now that the snort honeypot is listed in the sensor, I performed an attack using nmap, passing it the external IP of the snort honeypot VM. As a result in the Attacks page of the MHN Admin console, I was able to see my IP address listed with several port scan records which is the evidence that the honeypot intercepted my attack.
* Snort honeypot uses the TCP protocol
* This honeypot is attacked less frequently than others.

- [x] **GIF Walkthrough:**
<img src="snort-honeypot.gif">

### 2. p0f Honeypot

- [x] **Summary:**
* p0f is a tool that utilizes an array of sophisticated, purely passive traffic fingerprinting mechanisms to identify the players behind any incidental TCP/IP communications (often as little as a single normal SYN) without interfering in any way.
* Same as the other honeypots performed before, I created the VM for pOf honeypot called honeypot-3 make note of the external IP and established SSH access to the VM where I executed the deploy command for pOf that I copied from the MHN admin console.
* Now that the pOf honeypot is listed in the sensor, I performed an attack using nmap, passing it the external IP of the pOf honeypot VM. As a result in the Attacks page of the MHN Admin console, I was able to see my IP address listed with several port scan records which is the evidence that the honeypot intercepted my attack.
* pOf honeypot uses the pcap protocol

- [x] **GIF Walkthrough:**
<img src="p0f-honeypot.gif">


## Notes

At the beginning of this project, I tried to install GCP SDK on my local machine but it was not working properly in windows. After some failed attempt, I started to work with kali which was a lot easier. I initially tried installing all of these honeypots under kali 2022.3 version but realized the cowrie VM wasn't returning anything. Further inspection revealed that there are currently some deployment errors on this version of kali which is not allowing the cowrie VM. I did not wanted to harm the work I have done so far. So I killed the VM and tried the pOf VM, which resulted in success.
