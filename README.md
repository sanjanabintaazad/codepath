# Pen Testing Live Targets

Time spent: **17** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation



## Blue

#### Vulnerability 1: SQL Injection (SQLi)

- [x] Description:
  - If we put `'` in the id parameter of the URL and get database query failed, then the webpage is vulnerable to SQL injection.
  - Inserting `' OR SLEEP(5)=0--'` in the id parameter of the URL causes the webpage to sleep for 5 seconds, then shows the information of the user with id=1 by default.
  - Inserting `10' AND SLEEP(5)=0--'` in the id parameter of the URL causes the webpage to sleep for 5 seconds, then shows the information of the user with id 10.

- [x] GIF Walkthrough:
<img src="blue_SQLI_vulnerability.gif">


#### Vulnerability 2: Session Hijacking

- [x] Description:

- [x] GIF Walkthrough:
<img src="blue_SessionHijacking_vulnerability.gif">


## Green

#### Vulnerability 1: Cross-Site Scripting (XSS)

- [x] Description:

- [x] GIF Walkthrough:
<img src="green_XSS_vulnerability.gif">


#### Vulnerability 2: Username Enumeration

- [x] Description:

- [x] GIF Walkthrough:
<img src="green_UsernameEnumeration_vulnerability.gif">


## Red

#### Vulnerability 1: Insecure Direct Object Reference (IDOR)

- [x] Description:

- [x] GIF Walkthrough:
<img src="red_IDOR_vulnerability.gif">


## Notes

Describe any challenges encountered while doing the work
