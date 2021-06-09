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
<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&col-or=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>

### 2.2	Bully Chatbot – Coupon Code ★

### 2.3	Confidential Document – Sensitive Data Exposure ★

### 2.4	DOM XSS – Embedded a malicious script in the search function ★
<script>alert(xss)</script><br/>
<iframe src="javascript:alert(`xss`)">
 
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
  


  



