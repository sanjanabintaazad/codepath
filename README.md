# Project 7 - WordPress Pen Testing

Time spent: 26 hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pen Testing Report

### 1. CSRF

- [x] Summary: 
  - Vulnerability types: CSRF
  - Tested in version: 4.2
  - Fixed in version: 4.2.23
- [x] GIF Walkthrough: 
 ![Walkthrough exploit 1](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/1st%20vulnerability.gif)
- [x] Steps to recreate: 
  - Log in as Administrator
  - Post a comment to check it is taking the admin's comment
  - Submit a malicious form that goes into /wp-comments-post.php hosted on github
  - The comment "I made a comment" will be posted after going to the github link which is submitting the form (go below to Assets to see the malicious form)
- [x] Affected source code:
  - [Core Trac WordPress](https://core.trac.wordpress.org/changeset/44842)
  - [WordPress Github](https://github.com/WordPress/WordPress/commit/0292de60ec78c5a44956765189403654fe4d080b)
  
### 2. SOME (CVE-2016-4566)

- [x] Summary: 
  - Vulnerability types: Pupload Same Origin Method Execution (SOME)
  - Tested in version: 4.2
  - Fixed in version: 4.2.8
- [x] GIF Walkthrough: 
 ![Walkthrough exploit 2](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/2nd%20vulnerability.gif)
- [x] Steps to recreate: 
  - Insert a malicious code followed by a button and a script to the comment section of a post

      `<button onclick="fire()">Click</button>`

      `<script>
       function fire() {
       open('javascript:setTimeout("location=\'http://wpdistillery.vm/wp-includes/js/plupload/plupload.flash.swf?target%g=opener.document.body.firstElementChild.nextElementSibling.nextElementSibling.firstElementChild.click&uid%g=hello&\'",2000)');
       setTimeout('location="http://wpdistillery.vm/wp-admin/plugin-install.php?tab=plugin-information&plugin=wp-super-cache&TB_iframe=true&width=600&height=550"')
       }
       </script>`
  - Post the comment as admin
  - A button will appear as a comment
  - Click the button
  - It will ask us to download something
- [x] Affected source code:
  - [WordPress Github](https://github.com/WordPress/WordPress/commit/c33e975f46a18f5ad611cf7e7c24398948cecef8)
  - [Gist Github](https://gist.github.com/cure53/09a81530a44f6b8173f545accc9ed07e)

### 3. XSS (CVE-2015-3440)

- [x] Summary: 
  - Vulnerability types: Unauthenticated Stored Cross-Site Scripting (XSS)
  - Tested in version: 4.2
  - Fixed in version: 4.2.1
- [x] GIF Walkthrough: 
 ![Walkthrough exploit 3](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/3rd%20vulnerability.gif)
- [x] Steps to recreate: 
  - Go to "Hello world!" under RECENT POSTS
  - Reply to a comment by typing name, email and comment and see that it is waiting for the admin's approval after being post
  - Log in as Administrator
  - Approve the user and logout
  - Go back to the comment and reply using the same user name and email
  - Insert a malicious href link that sends an alert (go below to Assets to see the malicious href link's format)
  - The comment needs to be long enough so that it takes up the whole page
  - After posting the comment, moving the mouse above the page will trigger the alert
- [x] Affected source code:
  - [Exploit-db 36844](https://www.exploit-db.com/exploits/36844)
  - [Klikki's Exploit Code](https://klikki.fi/wordpress-4-2-core-stored-xss/)

### 4. XSS (CVE-2015-5734)

- [x] Summary: 
  - Vulnerability types: Legacy Theme Preview Cross-Site Scripting (XSS)
  - Tested in version: 4.2
  - Fixed in version: 4.2.4
- [x] GIF Walkthrough: 
 ![Walkthrough exploit 4](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/4th%20vulnerability.gif)
- [x] Steps to recreate: 
  - Log in as Administrator
  - Go to the Hello World post's comment section
  - Write the following maicilious code of a link that sends alert when scrolled above hello world in the page
 
      `<a href='/wp-admin/' title="XSS" style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(2)//'>Hello world</a>`
  - Post the malicious comment and watch the alert being triggered.
- [x] Affected source code:
  - [Core Trac WordPress](https://core.trac.wordpress.org/changeset/33549)
  - [Sucuri Blog](https://blog.sucuri.net/2015/08/persistent-xss-vulnerability-in-wordpress-explained.html)

### 5. XSS (CVE-2016-1564)

- [x] Summary: 
  - Vulnerability types: Authenticated Cross-Site Scripting (XSS)
  - Tested in version: 4.2
  - Fixed in version: 4.2.6
- [x] GIF Walkthrough: 
 ![Walkthrough exploit 5](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/5th%20vulnerability.gif)
- [x] Steps to recreate: 
  - Log in as Administrator
  - Go to the Hello World post's comment section
  - Write the following maicilious URL followed by an onload alert
  
    `http://wpdistillery.vm/<svg onload=alert(1)>`
  - Post the comment and it will trigger the alert
  - Everytime the page gets load, the alert will pop up
- [x] Affected source code:
  - [WordPress Github](https://github.com/WordPress/WordPress/commit/7ab65139c6838910426567849c7abed723932b87) 

## Assets

- 1st Vulnerability(Malicious Form):

      https://github.com/sanjanabintaazad/hello-world/blob/main/index.html
- 3rd Vulnerability:

      `<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>`


## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with
[ScreenToGif](https://www.screentogif.com/)

## Notes

The Correct installation of wordpress was a challenging task. As windows do not have Git I had to install it separately. I had a different IP address after pinging the [wpdistillery.vm](http://wpdistillery.vm/). That raised an issue with my host machine not being able to access the [wpdistillery.vm](http://wpdistillery.vm/) page. But it was running absolutely fine in Kali. After a long run and error trial, finally I was able to change IP address and run the wordpress in my host machine. Finding the vulnerabilities was a difficult task. I had to go through a lot of resources to understand the exploits. Once I figured out the concept and tricks I was able to find out 8 exploits. It was fun to do the extras.

## License

    Copyright [2022] [Sanjana Binta Azad]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
