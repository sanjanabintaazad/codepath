# Honeypot Assignment

**Time spent:** **15** hours spent in total

**Objective:** Create a honeynet using MHN-Admin. Present your findings as if you were requested to give a brief report of the current state of Internet security. Assume that your audience is a current employer who is questioning why the company should allocate anymore resources to the IT security team.

### MHN-Admin Deployment (Required)

- [x] **Summary:** How did you deploy it? Did you use GCP, AWS, Azure, Vagrant, VirtualBox, etc.?
* I deployed MHN-Admin in Kali by creating VM instances & using Google Cloud Services with the following honeypots: Dionaea, Snort & p0f.
* At first I created a google cloud account and then created a project.  

- [x] GIF Walkthrough:
<img src="mhn-admin.gif">

### Dionaea Honeypot Deployment (Required)

- [x] **Summary:** Briefly in your own words, what does dionaea do?

- [x] GIF Walkthrough:
<img src="dionaea-honeypot.gif">

### Database Backup (Required) 

- [x] **Summary:** What is the RDBMS that MHN-Admin uses? What information does the exported JSON file record?

*Be sure to upload session.json directly to this GitHub repo/branch in order to get full credit.*

### Deploying Additional Honeypot(s) (Optional)

#### Snort Honeypot

- [x] **Summary:** What does this honeypot simulate and do for a security researcher?

- [x] GIF Walkthrough:
<img src="snort-honeypot.gif">

#### p0f Honeypot

- [x] **Summary:** What does this honeypot simulate and do for a security researcher?

- [x] GIF Walkthrough:
<img src="p0f-honeypot.gif">


## Notes

At the beginning of this project, I tried to install GCP SDK on my local machine but it was not working properly in windows. After some failed attempt, I started to work with kali which was a lot easier. I initially tried installing all of these honeypots under kali 2022.3 version but realized the cowrie VM wasn't returning anything. Further inspection revealed that there are currently some deployment errors on this version of kali which is not allowing the cowrie VM. I did not wanted to harm the work I have done so far. So I killed the VM and tried the pOf VM, which resulted in success.
