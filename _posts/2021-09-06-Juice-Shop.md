---
title: Juice Shop Challenges
author: Diego Borghgraef
date: 2021-06-09 12:00:00 +0800
categories: [Security]
tags: [challenges]     # TAG names should always be lowercase
---

![image](https://user-images.githubusercontent.com/46396750/121337727-1fd1a680-c91d-11eb-90ef-8d336b61daa4.png)

## OWASP Juice Shop

Insecure web application used as security training/ guinea pig for security tools. 

### Setup
I installed the Insecure web application on Heroku. It was the quickest and easiest way to set it up.
I followed this installation [guide](https://bkimminich.gitbooks.io/pwning-owasp-juice-shop/content/part1/running.html).
Link to Heroku OWASP Juice shop app: https://owasp-juice-shop-diego.herokuapp.com/#/

## Challenges ★
### 2.1	Bonus Payload ★
```<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&col-or=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>
```

### 2.2	Bully Chatbot – Coupon Code ★

### 2.3	Confidential Document – Sensitive Data Exposure ★

### 2.4	DOM XSS – Embedded a malicious script in the search function ★
```<script>alert(xss)</script><br/>
<iframe src="javascript:alert(`xss`)">
```
 
![image](https://user-images.githubusercontent.com/46396750/121338666-ffeeb280-c91d-11eb-869f-cb01cc4b6a0a.png)

### 2.5	Error Handling ★

### 2.6	Exposed Metrics – Prometheus ★

  * Used to represent the number of requests serverd, tasks completed or errors.
  * https://owasp-juice-shop-diego.herokuapp.com/metrics
  * You can find all the metrics and how many time they occur.

### 2.7	Missing Encoding – Improper Input Validation ★
*	src="assets/public/images/uploads/😼-#zatschi-#whoneedsfourlegs-1572600969477.jpg"
*	The # is interpreted as HTML Anchors which is why the picture is not working.
*	We have the change with the right encoding
*	Change with %23 which the right encoding

### 2.8	Outdated Allowlist – Redirect to crypto currency address ★
  
  ![image](https://user-images.githubusercontent.com/46396750/121339101-6f64a200-c91e-11eb-8450-5b7b1efdfc4b.png)
 
*	Look in F12 (Developer Tools) at main.js files. They contain potential valuable information
*	When looking for redirects we can find Crypto wallets redirects.

### 2.9	Privacy Policy ★

### 2.10	Repetitive Registration – Improper Input Validation ★
*	False input in the Registration form
*	You can modify the first set of password and the registration will still be done.
*	After analyzing the last password is the password being used.

### 2.11	Score Board ★

### 2.12	 Zero Stars – Burp Suite Tamper data ★
*	Intercept request from contact from
*	Change values to 0 stars

## Challenges ★★

### 2.13	Depreciated Interface – Security Misconfiguration ★★
*	Using Burp intercept the request for a complain. Only allowed files are pdf & zip.
*	But when using Burp we can change our file type back to XML file.
*	Security Misconfiguration.
![image](https://user-images.githubusercontent.com/46396750/121339504-d97d4700-c91e-11eb-97cc-c3b5a8b9c9af.png)
![image](https://user-images.githubusercontent.com/46396750/121339519-dc783780-c91e-11eb-9d74-15f335be1c33.png)
 
### 2.14	 Login Admin ★★
*	‘—
  
### 2.15	Login MC SafeSearch ★★
*	mc.safesearch@juice-sh.op
*	Find his password listening to his song
*	Email found true the admin account /administration

  
### 2.16 Meta Geo Stalking – Sensitive Data Exposure ★★
*	With the use of Exiftools we can extract the coordinates of a picture.
*	Using this we got multiple different places.
*	Using Burp Suite we tried the multiple possibilities until we managed to change the password.
  ![image](https://user-images.githubusercontent.com/46396750/121339701-09c4e580-c91f-11eb-989d-94c07afe7b63.png)
 
### 2.17	Password Strength – Broken Authentication ★★
*	admin@juice-sh.op:admin123
 
### 2.18 SQL Injection – Access Admin Login ★★
*	‘ OR true
*	Check console logs for error messages.

### 2.19	Horizontal Privilege escalation – Broken Access Contol ★★
*	Basket – Add products.
*	F12 Developer tools
*	“Application” – SessionStorage
*	Change “bid” value – Gives you information about other people’s basket.

  
![image](https://user-images.githubusercontent.com/46396750/121339930-4a246380-c91f-11eb-89bd-ee2a73500ab4.png)

  
### 2.20	Security Policy ★★
![image](https://user-images.githubusercontent.com/46396750/121339978-56a8bc00-c91f-11eb-876a-0da679d1b21e.png)
*	You can find Security Policies by looking at the security.txt file. Most of the time you can find it at /.well-known/security.txt

  
### 2.21	Visual Geo Stalking – Sensitive Data Exposure ★★
  
### 2.22	Visual Geo Staking – Sensitive Data Exposure ★★
  
### 2.23	Weird Crypto – Cryptographic Issues ★★
*	Contact support for bad hash algorithm.
*	MD5 not secure

## Challenges ★★★
### 2.24	Admin Registration – Improper Input Validation ★★★
![image](https://user-images.githubusercontent.com/46396750/121340094-7c35c580-c91f-11eb-9a3d-b1e5ada39be3.png)
*	Using Burp Suite Intercept an Registration form 
*	Find the /api/Users
*	You find all the information about a users registration
*	When look at the response you see there is a role option
*	By default its set to “customer”
*	When we a repeater attack we can modify the Request to add a role of Admin
*	When sending the requests we get a new user with admin roles. 

### 2.25	Forged Feedback – Broken Access Control ★★★
*	Customer Feedback
*	Find hidden form
*	Change default value 49 -> 1
*	Message send as Admin
  
![image](https://user-images.githubusercontent.com/46396750/121340236-a8e9dd00-c91f-11eb-907b-51f77a854041.png)

### 2.26	Bjoern’s Favorite Pet – Broken Authentication ★★★
*	https://www.youtube.com/watch?v=Lu0-kDdtVf4
*	Looking at this video from Bjoern on the public internet you can see his registration using Bjoern@owasp.org with the security question being Zaya.
![image](https://user-images.githubusercontent.com/46396750/121340256-b2734500-c91f-11eb-9bdf-a4f0390a8745.png)
  
### 2.27	CAPTCHA Bypass – Broken Anti Automation ★★★
*	Submit 10 or more customer feedbacks within 10 seconds.
*	Very interesting challenge
*	First I intercepted a request using Burp Suite.
*	I then used in the repeater and found out that the captcha will always be successful with the same CaptchaID en CaptchaCode.
*	Using the Intruder I perfomed 10 attacks which each time different values.
*	CAPTCHA is not secure as it is linked with a certain id.
  
![image](https://user-images.githubusercontent.com/46396750/121340327-c8810580-c91f-11eb-869b-451014833d6c.png)![image](https://user-images.githubusercontent.com/46396750/121340340-cc148c80-c91f-11eb-8119-a6bc9dbc6a63.png)
 
### 2.28	CSRF – Broken Access Control ★★★
*	Cross-Site Request Forgery
*	http://htmledit.squarefree.com/

```<html>
<body>
<form action="https://owasp-juice-shop-diego.herokuapp.com/profile" method="POST">
<input type="hidden" name="username" value="tedddt">
<input type="submit" value="Set Username">
</form>

</body>
</html>

<script>
xmlhttp = XMLHttpRequest;
xmlhttp.open('GET', 'http://owasp-juice-shop-diego.herokuapp.com/rest/user/change-password? new=1234567&repeat=1234567');
xmlhttp.send()
</script>
```
  
### 2.29	Database Schema – Injection (DIFFICULT) ★★★
```GET /rest/products/search?q=apple'))UNION%20SELECT%20sql,2,3,4,5,6,7,8,9%20FROM%20sqlite_master-- HTTP/1.1
Host: owasp-juice-shop-diego.herokuapp.com
Connection: close
sec-ch-ua: "Chromium";v="89", ";Not A Brand";v="99"
Accept: application/json, text/plain, */*
sec-ch-ua-mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.128 Safari/537.36
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://owasp-juice-shop-diego.herokuapp.com/
Accept-Encoding: gzip, deflate
Accept-Language: nl-NL,nl;q=0.9,en-US;q=0.8,en;q=0.7
```

*	Using burp we find out it is a SQLlite database
*	Using the ‘)) after the search we can start a new query
*	We use the UNION to start a second query
*	%20 is a html character for “space”
*	SELECT sql FROM sqlite_master, gives us a schema of all the different tables on the website.
https://www.youtube.com/watch?v=0-D-e66U2Z0
  
### 2.30	Deluxe Fraud – Improper Input Validation ★★★
Obtain a Deluxe Membership without paying for it.
 ![image](https://user-images.githubusercontent.com/46396750/121341070-97ed9b80-c920-11eb-85e8-c6cfe05d4247.png)
*	When unlocking the button for paying through the wallet
*	I get a request with PaymentMode: “wallet”
*	By changing the request in the repeater with “paid” we get a Deluxe Membership.

  
### 2.31	Forged Feedback – Broken Access Control ★★★
 ![image](https://user-images.githubusercontent.com/46396750/121341124-a5a32100-c920-11eb-8ef5-06c3eca685cb.png)

*	When inserting the Feedback into Burp, we can see the request being sent.
*	Reading the Response form we see there is a value UserId.
*	By modifying the Request and adding a UserId we can change from who the message is being sent.

  ![image](https://user-images.githubusercontent.com/46396750/121341133-a76ce480-c920-11eb-9a3a-2a4c45812482.png)

### 2.32	Forged Review – Broken Access Control ★★★
![image](https://user-images.githubusercontent.com/46396750/121341174-b18ee300-c920-11eb-89d0-e1481229ecd0.png) 
*	Same situation as the Forged Feedback.
*	In BurpSuite I changed the “author” with my email address.

  
### 2.33	GDPR Data Erasure – Broken Authentication ★★★
![image](https://user-images.githubusercontent.com/46396750/121341202-b9e71e00-c920-11eb-8572-83029f2a1b07.png)
*	Right for erasure with each user.
*	But when performing SQL injection we can connect on someone account and perform a data eras-ure

  
### 2.34	Login Jim – SQL Injection ★★★
*	Jim@juice-sh.op ‘—
*	Avoids putting the login password
![image](https://user-images.githubusercontent.com/46396750/121341258-c5d2e000-c920-11eb-8354-7fa240caa3f5.png)

  
### 2.35	Login Bender – SQL Injection ★★★
*	Bender@juice-sh.op ‘—
![image](https://user-images.githubusercontent.com/46396750/121341293-cec3b180-c920-11eb-8b0b-b830a50fec48.png)
  
### 2.36	Login Amy – Sensitive Data Exposure ★★★
*	Looking at the link: https://www.grc.com/haystack.htm
*	We find information about possible good passwords
*	With the knowledge from the tutorial we know amy has a boyfriend named kif
*	D0g..................... --> K1f.....................


### 2.37	Manipulate Basket – Broken Access Control ★★★
When adding product to your basket you can added BasketIds from other persons. This gives the possibility to checkout with multiple baskets.
  
### 2.38	Payback Time – Improper Input Validation ★★★
When adding a product to your basket you get a request for the quantity. You can change the quantity to a negative number, which gives you the possibility to have -100 in quantity. When ordering the products you actually get money back !
![image](https://user-images.githubusercontent.com/46396750/121341363-e13deb00-c920-11eb-8838-e9ff3ffff89a.png)

  
### 2.39	Privacy Policy Inspection – Security Through Obscurity ★★★
  
### 2.40	Product Tampering – Broken Access Control ★★★
When looking at the review page of a product, you get information about it. Changing the request to a PUT request on the API and only change the description information. So that when you click on the more button the href changed to owasp.slack.

  
### 2.41	Reset Jim’s Password – Broken Authentication ★★★
Reference to Startrek.

  
### 2.42	Upload Size – Improper Input Validation ★★★
Change the data inserted in the request with a file higher than 100kb. This gives us the possibility to upload bigger files.
 ![image](https://user-images.githubusercontent.com/46396750/121341410-ec911680-c920-11eb-86e4-3ed04d83d235.png)
 
### 2.43	Upload Type – Improper Input Validation ★★★
For the upload type, I uploaded the file using the .exe.pdf extension, so it accepts the file on request. After setting it up in the repeater I removed the .pdf so that the .exe could be executed.

  ## Challenges ★★★★
### 2.44	 Access Log – Sensitive Data Exposure ★★★★
https://owasp-juice-shop-diego.herokuapp.com/support/logs
  
### 2.45	Allowlist Bypass – Unvalidated Redirects ★★★★
https://owasp-juice-shop-die-go.herokuapp.com/redirect?to=diegoborghgraef.be?pwnd=https://blockchain.info/address/1AbKfgvw9psQ41NbLi8kufDQTezwG8DRZm

  
### 2.46	Christmas Special – Injection ★★★★
  ![image](https://user-images.githubusercontent.com/46396750/121341528-0c283f00-c921-11eb-96f6-42f43cab8089.png)

First I createda SQL Injection using the known ‘))—request which gives me information about all the prod-ucts in the shop. We found out that the Christmas Special is id 10. With this information we created a new request when adding a product in the cart but changed the ProductId with the id 10. When added in the bas-ket we ordered the product using the – quantity exploit which gave us a free order.
  ![image](https://user-images.githubusercontent.com/46396750/121341544-0fbbc600-c921-11eb-8f9c-cbf1f86d6464.png)


  
### 2.47	Easter Egg – Broken Access Control ★★★★
 ![image](https://user-images.githubusercontent.com/46396750/121341584-18140100-c921-11eb-834c-bb3854e37214.png)
https://owasp-juice-shop-diego.herokuapp.com/ftp/eastere.gg%2500.md

We can find a lot of files in the ftp folder, but the problem is that we are only allowed to download .md & .pdf files. When modifying the request URL we added some HTML encode %25 and then added .md Now the file is available to download.
![image](https://user-images.githubusercontent.com/46396750/121341615-1e09e200-c921-11eb-82ce-2faaf5bd3704.png)
NULL BYTE INJECTION (%00)
  
### 2.48	Ephemeral Accountant – Injection ★★★★
  
### 2.49	Expired Coupon – Improper Input Validation ★★★★
When looking at the JavaScript file you can find information about all the available coupons. The problem is that they are not working anymore. Because they were only available for 1 day. When changing our Operat-ing systems time to the right date and apply the coupon we can see it working.
  ![image](https://user-images.githubusercontent.com/46396750/121341662-29f5a400-c921-11eb-8ae7-d781d290f4d8.png)

  
### 2.50	Forgotten Developer Backup – Sensitive Data Exposure ★★★★
https://owasp-juice-shop-diego.herokuapp.com/ftp/package.json.bak%2500.md
  
### 2.51	Forgotten Salesman Backup – Sensitive Data Exposure ★★★★
http://localhost:3000/ftp/coupons_2013.md.bak%2500.md

  
### 2.52	GDPR Data Theft – Sensitive Data Exposure ★★★★
  
### 2.53	Leaked Unsafe Product – Sensitive Data Exposure ★★★★
  ![image](https://user-images.githubusercontent.com/46396750/121341888-632e1400-c921-11eb-9cf0-75c253aee713.png)

### 2.54	Legacy Typosquatting – Sensitive Data Exposure ★★★★
Typosquatting is een vorm van misbruik van het internet gebaseerd op het feit dat mensen zich weleens vergissen bij het intypen van een websiteadres. De typosquatter zet een website op, waarvan het adres (domeinnaam) slechts heel weinig verschilt van het adres van een populaire website. Alle internetgebrui-kers die dezelfde typefout of vergissing maken, komen terecht op de website van de typosquatter.
 ![image](https://user-images.githubusercontent.com/46396750/121341908-69bc8b80-c921-11eb-83b4-d400ab69aabc.png)

In the Developers backup file you find alle the dependencies used on the OWASP JuiceShop. 1 depency was not the right one. Epilogue-js is not the real epilogue. This is due to someone typosquatting.

  
### 2.55	Login Bjoern – Broken Authentication ★★★★
  
### 2.56	Misplaced Signature File – Sensitive Data Exposure ★★★★
Sigma is a generic and open signature format that allows you to describe relevant log events in a straight-forward manner. The rule format is very flexible, easy to write and applicable to any type of log file. The main purpose of this project is to provide a structured form in which researchers or analysts can describe their once developed detection methods and make them shareable with others.

  SIEM SIGNATURE.
	ACCESS .YML FILE : https://owasp-juice-shop-diego.herokuapp.com/ftp/suspicious_errors.yml%2500.md

  
### 2.57	Nested Easter Egg – Cryptographic Issues ★★★★
L2d1ci9xcmlmL25lci9mYi9zaGFhbC9ndXJsL3V2cS9uYS9ybmZncmUvcnR0L2p2Z3V2YS9ndXIvcm5mZ3JlL3J0dA== (Code found in the FTP folder)

When decoding it in Base 64. You get a path. But the words do not mean anything.
Using a online decipher tool. We found a matching deciphering technique that gave us the path we wanted. 

https://owasp-juice-shop-diego.herokuapp.com/the/devs/are/so/funny/they/hid/an/easter/egg/within/the/easter/egg
  
### 2.58	NoSQL Manipulation – Injection ★★★★
https://www.netsparker.com/blog/web-security/what-is-nosql-injection/
Target databases that do not use the sequal database model
  ![image](https://user-images.githubusercontent.com/46396750/121342007-85c02d00-c921-11eb-9c29-345945bed789.png)


  
### 2.59	Poison Null Byte – Improper Input Validation ★★★★
%2500.md

  
### 2.60	Reset Bender’s Password – Broken Authentication ★★★★
   
### 2.61	Reset Uvogin’s Password – Sensitive Data Exposure ★★★★
  
### 2.62	Steganography – Security Through Obscurity ★★★★
Steganography, partice of concealing a message within another message or a physical object. In computer file, message, image or video is concealed within another file. 

For this challenge we get a hint that we need to look for the Lorem Ipsum. We know that a Lorem Ipsum text is available on the About Us page. There we can find a slideshow of multiple pictures of users. Be-cause we are working with Steganography is used the Openstego tool to try to read each picture. Some-thing I didn’t know is that 1 image had a .png format and there we found a steganography.

It was a Image of Pickle Rick! We then sended a Customer Feedback with Pickle Rick to get the challenge done.
 <br/> 
  ![image](https://user-images.githubusercontent.com/46396750/121342082-996b9380-c921-11eb-9c9d-f967c0c63577.png)


  
### MORE COMING SOON
  
 


  


  



