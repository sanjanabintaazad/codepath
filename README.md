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

- [x] **Summary:** Briefly in your own words, what does dionaea do?
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

- [x] **Summary:** What is the RDBMS that MHN-Admin uses? What information does the exported JSON file record?

*Be sure to upload session.json directly to this GitHub repo/branch in order to get full credit.*

## Deploying Additional Honeypot(s) (Optional)

### 1. Snort Honeypot

- [x] **Summary:** What does this honeypot simulate and do for a security researcher?

- [x] **GIF Walkthrough:**
<img src="snort-honeypot.gif">

### 2. p0f Honeypot

- [x] **Summary:** What does this honeypot simulate and do for a security researcher?

- [x] **GIF Walkthrough:**
<img src="p0f-honeypot.gif">


## Notes

At the beginning of this project, I tried to install GCP SDK on my local machine but it was not working properly in windows. After some failed attempt, I started to work with kali which was a lot easier. I initially tried installing all of these honeypots under kali 2022.3 version but realized the cowrie VM wasn't returning anything. Further inspection revealed that there are currently some deployment errors on this version of kali which is not allowing the cowrie VM. I did not wanted to harm the work I have done so far. So I killed the VM and tried the pOf VM, which resulted in success.
