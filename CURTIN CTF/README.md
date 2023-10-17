# Curtin CTF 2023
![2](https://github.com/plnsgr/os1ris/blob/main/CURTIN%20CTF/images/image002.jpg?raw=true)


Welcome to the Curtin CTF 2023 writeup challenge! In this repository, you will find writeups and solutions for various challenges presented during the competition. Feel free to explore the challenges and learn from the writeups provided here.

## Navigate

- [General Web](#general-web)
- [SQLi](#sqli)
- [Crypto](#crypto)
- [Forensics](#forensics)
- [Pwn & Reverse Eng](#pwn--reverse-eng)
- [OSINT](#osint)
- [General](#general)

---

## General Web
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Content Missing – I

(Author: 4jai)

![3](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image003.png)

This challenge is continuity for Content Missing – II, but I don’t know why it’s name I. So anyway, we found the suspicious directory in the headphone photo named /homeChall. When we try to access the webpage, it just says the flag for this challenge.

![4](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image004.png)

But when accessing using curl, there are hidden directory in the response.

![5](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image005.png)

So, we try to access the hidden directory and get the flag.

![6](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image006.png)

```
Flag: CURTIN_CTF{C0NGR4TUL4T10N5_0N_Y0UR_H0M3C0M1NG}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Content Missing – II

(Author: 4jai)

![7](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image007.png)

These challenges ask us to find missing content in the webpage, so we can analyze the source code to find any suspicious code here. We found something unusual at the fourth photo.

![8](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image008.png)

Based on the image, it should be in /static/Content.png but the code shows that we cannot find the image. So, we try to look in the /static and there are Content.png with the flag.

![9](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image009.png)

```
Flag: CURTIN_CTF{N33D_F0R_B3TT3R_C0D3_R3V13W}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### No Crawl

(Author: 4jai)

![10](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image010.png)

This challenge was straight forward as it just give us a website. The challenge name was the clue for our investigation, and it was the crawler. Google crawler will crawl to website and there are one file that use to navigate the crawler called robots.txt.

![11](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image011.png)

There are hidden directory here and we got the flag from the directory.

![12](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image012.png)

```
Flag: CURTIN_CTF{B0T530T5BOTSB0T555555BOTS}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Join the Union

(Author: 4jai)

![13](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image013.png)

In this challenge we were given the webpage to register.

![14](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image014.png)

After we tried to register, we also intercept the request using burp and we found interesting directory.

![15](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image015.png)

We can try to access the directory, but it asks me WHO AM I. Whut. After some experiments, we can see that there is cookie value that may be useful. I first didn’t know what to do with that value but after some experiment with the request, we got the flag.

![16](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image016.png)

```
Flag: CURTIN_CTF{Th15_Fl4g_15_h15hly_c0nf1d3nt14l}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Hackerman

(Author: 4jai & OS1RIS)
![17](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image017.png)

This webpage is straight forward as we need to login using Username Hackerman and unknown password. 
Looking through source code, the password may have some criteria to be follow.

![18](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image018.png)

This JavaScript show that the password needs to be 10 characters in length and including number and . symbol. So base on the clue given the password are the pi value. Because in the pie there is a dot and fit the authors quote has the clue "Circle".

![19](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image019.png)

![20](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image020.png)
```
Password: 3.14159265
```
![21](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image021.png)

```
Flag: CURTIN_CTF{RUNN1NG_!N_C1Rcl3s_4ll_th3_t1M3}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Obscure Communication

(Author: OS1RIS)

![22](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image022.png)

Google-fu all available information then narrow down to more specific info/clue. It can be based on question name, author, category, related past ctf, etc . "Obscure" means something is not clear or easily understood. In this context, it might refer to a technique or method used to make the ETag value less predictable or harder to guess. Etag can setup the range such as Start and End range. With the buffer, it will read the content inside.

![23](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image023.png)

```
Flag: CURTIN_CTF{Th3_D3v1l15_1NTH3_D3T41L5}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## SQLi

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Try to login

(Author: 4jai)

![24](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image024.png)

The webpage ask us to login, by using simple payload ‘OR 1=1-- - in username and password, we got the flag.

```
‘OR 1=1-- -
```

![25](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image025.png)

```
Flag: CURTIN_CTF{5H0pT1m3}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Try logging in... again

(Author: 4jai)

![26](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image026.png)

The second webpage also ask the same questions, but now the payload did not work. We try to search another working payload and found the payload that can be use:

```
admin') or ('1'='1
```

![27](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image027.png)

```
Flag: CURTIN_CTF{welc0m3aG@1n}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Database Discovery Quest
(Author: 4jai)
![28](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image028.png)
![29](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image029.png)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Table Name Treasure Hunt
(Author: 4jai)
![30](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image030.png)
![31](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image031.png)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Fiver Fever
(Author: 4jai)
![32](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image032.png)
![33](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image033.png)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Slow Down...
(Author: 4jai)
![34](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image034.png)
![35](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image035.png)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Unveiling the Dark Wizard's Secrets
(Author: 4jai)
![36](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image036.png)
![37](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image037.png)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## Crypto
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Cryptography Warm Up – 1
(Author: OS1RIS)
![38](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image038.png)
![39](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image039.png)
![40](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image040.png)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Rock Solid Algorithm
(Author: OS1RIS)
![41](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image041.png)
![42](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image042.png)
![43](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image043.png)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### IV League Aesthetics
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Fun with Primes – 1
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### The Curse of Genius
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Cryptography Warm Up – 2
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Listening Skills
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Curvy Vibes
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Operational Duties
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### The Gambler’s Secret
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## Forensics
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Hide and Seek
(Author: 4jai)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Let's Analyze
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Secret File
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Nice Image!!!
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Nice Image - 2 !!!
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Soundless
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Party All Night – 2
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Weird Text
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Hoax
(Author: 4jai)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## Pwn & Reverse Eng
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Intro to Buffer Overflow
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Let The Random Games Begin 1
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Don't go overboard
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Don't go overboard 2
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Let The Random Games Begin 2
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Classic Buffer Overflow
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Let The Random Games Begin 3
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## OSINT
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Party All Night 1
(Author: Dinze)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Party All Night 3
(Author: Dinze)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Party All Night 4
(Author: OS1RIS)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### The Leaked IP
(Author: Dinze)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## General
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Feedback!!!
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Welcome !!!
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
