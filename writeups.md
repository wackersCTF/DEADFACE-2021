# Writeups for Challenges
Categories (and number of challenges solved)
* Starter/Bonus (1/1)
* Cryptography (5)
* Exploitation (1)
* Forensics (2)
* Network Analysis (3)
* OSINT (2)
* Programming (1)
* Reverse Engineering (2) 
* SQL (4)
* Steganography (4)

---

# Starter/Bonus
## Starter - 10 points
Hello there! We're so glad you're able to help us thwart DEADFACE this year. Let's get you spun up on where to get started.

We found out DEADFACE is likely targeting a company called De Monne Financial. They've targeted them in the past and based on some OSINT research, we're sure they're targeting De Monne again this year.

One of our partners found a forum page where DEADFACE discusses their activity. We managed to gain access to the forum and opened it up to be viewed publicly, but you won't be able to create an account. The forum site is called [Ghost Town](https://ghosttown.deadface.io/). There's a lot of information on this forum that might help you.

> Thanks for participating in this year's DEADFACE CTF! Before you begin, please take a look at our [rules](https://deadface.ctfd.io/rules) and submit the flag found on that page. Submitting the flag is an acknowledgement of the rules and your compliance. Thank you and enjoy the CTF!

### Writeup
At the bottom of the rules page, we see our flag. 

Flag: ```flag{themz_the_ru1es}```

## Jailbird - 20 points
It looks like authorities arrested a member of DEADFACE. But who was it?

Submit the member's username as the flag: `flag{username}`

### Writeup
Searching up "arrest" in the forum shows a thread with an article. In the article, a man named Donnell Aulner has been arrested as a culprit of the database leak. Underneath the article link, there's a comment saying "Yep, @dr.acula … I’m so pissed rn…" We can assume that this is the username of Donnell. 

Flag: ```flag{dr.acula}```

---

# Cryptography
## Big Boss - 10 points
An anonymous tipster sent us this photo alleging that it's a note written by **b3li3f1203**. The tipster claims that the note was intended for someone who works at De Monne Financial. They also said it's likely that it has something to do with a phishing campaign. Provide the name of the target individual as the flag in this format: `flag{FirstName_LastName}`.

### Writeup
The ciphertext is ```Hvs bslh asshwbu kwzz ps hcrom oh bccb. Bssr hc twbr cih Xwaaws'g kcfy gqvsrizs gc ks ybck kvsb wg psgh hc dvwgv vwa. Hvs qoadowub bssrg hc zccy zwys wh qoas tfca vwg pcgg, Aofqig PmbsF. Vs kcfyg og ob Orjobqsr Gczihwcbg GidsfjwgcF - rcb'h tcfush hc wbqzirs hvoh wb hvs saowz.```

Using [quipqiup](https://quipqiup.com), we can easily crack this substitution cipher.

The decrypted plaintext is ```The next meeting will be today at noon. Need to find out Jimmie's work schedule so we know when is best to phish him. The campaign needs to look like it came from his boss, Marcus Byner. He works as an Advanced Solutions Supervisor - don't forget to include that in the email.```.

Flag: ```flag{Marcus Byner}```

## Poor MEGAN! - 20 points
Oh, NO! Poor Megan! She's just been bitten by a ZOMBIE! We can save her if we act fast, but the formula for the antidote has been scrambled somehow. Figure out how to unscramble the formula to save Megan from certain zombification. Enter the answer as `flag{here-is-the-answer}`.

The formula for the antidote:`j2rXjx9dkhW9eLKsnMR9cLDVjh/9dwz1QfGXm+b9=wKslL1Zpb45`

### Writeup
Plugging the ciphertext into Cyberchef, we are recommended a variation of the Base64 cipher named Megan35. [Link to recipe](https://gchq.github.io/CyberChef/#recipe=From_Base64('3GHIJKLMNOPQRSTUb%3DcdefghijklmnopWXYZ/12%2B406789VaqrstuvwxyzABCDEF5',true)&input=ajJyWGp4OWRraFc5ZUxLc25NUjljTERWamgvOWR3ejFRZkdYbStiOT13S3NsTDFacGI0NQ)

Flag: ```flag{Six-Parts-Honey-One-Part-Garlic}```

## To Be Xor Not to Be - 75 points

.$)/3<'e-)<e':e&'<e<'e-)<5

Submit the flag as `flag{here-is-the-answer}`

### Writeup
We can use a [XOR cipher decoder](https://www.dcode.fr/xor-cipher). Bruteforcing the key gives us our flag. 

Flag: ```flag{to-eat-or-not-to-eat}```

## A(n) [ENCRYPTED] by Any Other Name - 100 points

An encrypted message from **spookyboi** has been intercepted by law enforcement, but it is encrypted with an unknown algorithm and an unknown password. We know that he likes to speak in riddles, so perhaps he gave a riddle to one of his cohorts so they would know how to decrypt the message. Discover the algorithm and password, then decrypt the message below. Enter the flag as `flag{this-is-the-flag}`.

(Hint: We know that the message is encrypted with Electronic Code Book [ECB] cipher block mode, and we know that the password is in lower case.)

```base64
AmYiuw8WHXEpsgNZzGURwW7pXb6APcp7v4HWPzXirriOP3q3fFtCssImT5LR+edaN1k1+lBTbW1rjY/wZSIsPjmY2LOk2FuRBk9i0K25iolP5jtJBt+HyhWZ3EadYNNE24pG6o+znsseud9DIE3zaIObkMFBj6xsWVrhALpju4cJrQpoo74MlJ7cHURHkOC7cKdsMo5kdYA4CpHCEhljvfNSR82nM4Ee9HaVMO58/okaoAtfGadMZcLVadut5sJfVzLzzG0G+QLOAkD/qPtfixggtuDURXkHQ0m2KANEi/3+478bhPoX4AciR5DSRw5zvsuF9JFEu7UCa39KggeAIB0dayX2Ho7hCI2zWTAt+q1WKX8V55toBQd6wtA+fjAsNtLzuzMKhlg6bP7HIzSH8V81C+ocTcTLo5Ijy/ZKaQt7XcDmdRsPVJihQqMu5Pw+5BKbjVNsFL4dcNRfNr4dNQ==
```

### Writeup
The riddle is "Hey, @mort1cia, here’s the hint for the encrypted message I sent you. I used my favorite algorithm, and a special password (which you should get from the hint): Algorithm: a homonym of Password: a synonym of Spook, Spectre, Spirit, Phantasm Once used by an enemy, then “friend” to me, then “frenemy” I sent the message is “out-of-band”, so it will be impossible to intercept."

 Using this [website](https://www.tools4noobs.com/online_tools/decrypt/) and hints from the clue, we figure out the password is ghost and the algorithm is GOST.
 
 Decrypted text:
 ```The hack on Lytton Labs is going down at 11:59 PM, October 31, 2021.  Be ready with the custom ransomware.  We will upload it to their servers and unleash it in a scripted, coordinated attack!  Make sure to have at least five other hackers assist you with this.  thezealot is coordinating this operation.

flag{the-USSR-is-the-GOST-with-the-MOST}
```

 Flag: ```flag{the-USSR-is-the-GOST-with-the-MOST}```
 
 ## He Thrusts His Fists Against the Post - 100 points
{ea-vetgaytereoreh-na}fan--wshbestpasslds-s-hm

### Writeup
In the challenge description, we see a picture of a fence. Thus, we can infer that this is a railfence cipher. Decrypting it using [Rumkin](http://rumkin.com/tools/cipher/railfence.php) with 4 rails and offset of 2, we get our flag. 

Flag: ```flag{and-yet-swears-he-observes-the-phantasms}```

---

# Exploitation
## Password Insecurities - 50 points

It looks like DEADFACE is going after the password of one of De Monne's customers: Haily Poutress. She has since changed her password, but De Monne is looking for ways to improve password requirements. De Monne would like you to crack the password from the database leak to determine if Haily's password was secure enough. Submit the flag as `flag{password}`.

Use the MySQL database dump from **Body Count**.

### Writeup
We find our hash, ```$1$FigUPHDJ$IYWZKYxoKDdLyODRM.kQq.```, in the SQL database. Looking at our hash, we can figure out that it is encrypted using md5crypt, MD5 (Unix), or Cisco-IOS since it starts with a \$1$. For [hashcat](https://hashcat.net/wiki/doku.php?id=example_hashes), this is mode 500. 

We will run a simple straight attack (```-a 0```) with the rockyou.txt wordlist. 
Command: ```hashcat -a 0 -m 500 hashes.txt rockyou.txt```

The password is ```trustno1```.

Flag: ```flag{trustno1}```

---

# Forensics
## Blood Bash - 10 points
We've obtained access to a system maintained by bl0ody_mary. There are five flag files that we need you to read and submit. Submit the contents of `flag1.txt`.

Username: `bl0ody_mary`  
Password: `d34df4c3`

`bloodbash.deadface.io:22`

### Writeup

Given login information, we can assume this challenge is asking us to use SSH. The command format is ```ssh [username]@[address] -p [port number]```, so we type in
```ssh bl0ody_mary@bloodbash.deadface.io -p 22``` and login with the given password.

Now that we connected to the system, we need to search for this flag file. We use the command ```ls``` to list the files and directories in our current directory. We see a pdf file and 5 directories. They are Documents, Downloads, Music, Pictures, and Videos. Going inside the Documents directory, we find our file. Using the command ```cat flag1.txt```, we get our flag.

Flag: ```flag{cd134eb8fbd794d4065dcd7cfa7efa6f3ff111fe}```

## Blood Bash 2 - 15 points
We've obtained access to a system maintained by bl0ody_mary. We believe bl0ody_mary stole a sensitive document and is storing it on her Linux machine. Search her system for any files relating to De Monne Financial.

Username: `bl0ody_mary` Password: `d34df4c3`

`bloodbash.deadface.io:22`

### Writeup
We see a pdf file named ```'De Monne Customer Portal.pdf'```. After few attempts, I was unable to view the contents of this pdf file. Commands like pdf2text and scp were unavailable. 

So, I tried ```find / flag``` to search the entire file system for a flag. At the bottom of my result, I see this hidden file ```/home/bl0ody_mary/Documents/.demonne_info.txt```. Using the command ```cat /home/bl0ody_mary/Documents/.demonne_info.txt```, we get our flag.

Flag: ```flag{a856b162978fe563537c6890cb184c48fc2a018a}```

---

# Network Analysis
## Monstrum ex Machina - 30 points
Our person on the "inside" of Ghost Town was able to plant a packet sniffing device on Luciafer's computer. Based on our initial analysis, we know that she was attempting to hack a computer in Lytton Labs, and we have some idea of what she was doing, but we need a more in-depth analysis. This is where YOU come in.

We need YOU to help us analyze the packet capture. Look for relevant data to the potential attempted hack.

To gather some information on the victim, investigate the victim's computer activity. The "victim" was using a search engine to look up a name. Provide the name with standard capitalization: `flag{Jerry Seinfeld}`.

### Writeup
Looking at HTTP traffic (File -> Export Objects -> HTTP) in Wireshark, we see searches for a Charles Geschickter.

Flag: ```flag{Charles Geschickter}```


## Luciafer's Fatal Error - 50 points
Luciafer, consummate hacker, got cocky and careless. She made a fatal mistake, and in doing so, gave control of her computer to... someone. She ran a program on her computer that she shouldn't have.

What is the md5sum of the program? Submit the flag as: `flag{MD5}`.

### Writeup
Downloading all the files from the HTTP traffic, we see a file named secret_decoder.bin. We use an online md5 hash generator.

Flag: ```flag{42E419A6391CA79DC44D7DCEF1EFC83B}```


## A Warning - 150 points
Luciafer is being watched! Someone on the inside of Lytton Labs can see what she is doing and is sending her a message.

One of them says: "Stay away from Lytton Labs... you have been warned."

To find the flag, find the message. You'll know it when you see it. Submit the flag as `flag{flag-goes-here}`.

Use the PCAP from **LYTTON LABS 01 - Monstrum ex Machina**.

### Writeup
Downloading all the files from the HTTP traffic, we see an image file named "da-warning-message.jpg" Inside it is a message, "Fools rush in headlong where flag{angels-fear-to-tread}... TURN BACK NOW!"

Flag: ```flag{angels-fear-to-tread}```

---

# OSINT
## Meetup - 20 points
A member of DEADFACE suggested that they all meet up at some point. With this information, we'd be able to contact law enforcement to get them all at once! What does the picture say about their meetup location, though?

Submit the flag as: `flag{location}`.

Example: `flag{Golden Gate Bridge}`.

### Writeup

Using a Reverse Image Search like [TinEye](https://tineye.com) shows that the photo is from the Eastern State Penitentiary.

Flag: ```flag{Eastern State Penitentiary}```

## Occupation  - 20 points
Which employee at De Monne Financial was the target of DEADFACE that resulted in a data leak? Submit the employee's job title as the flag: `flag{Job Title}`

### Writeup

We search "leak" in the given forum and find this [post](https://ghosttown.deadface.io/t/they-got-the-wrong-guy/75). In the linked [article](https://www.worldgreynews.com/details/168914/de-monne-senior-organizer-on-administrative-leave-pending-data-leak-investigation), we find out that Jimmie Castora was the target. Googling his name yields his [LinkedIn account](https://www.linkedin.com/in/jimmie-castora-7a6170220/) which lists his job.

Flag: ```flag{Senior Directives Organizer}```

---
# Programming
## Unfinished - 5 points
There seems to be something wrong with this code. Can you figure out how to make it return the flag? Modify the code to show the flag. Submit the flag as: `flag{flag-goes-here}`.

```python
#!/usr/bin/env python3
from binascii import unhexlify as u

def get_flag():
    flag = '666c61677b30682d6c6f6f6b2d612d466c61477d'
    return u(flag).decode('utf-8')


print(f'The flag is: ')
```

### Writeup
We see that the code does not run the function and print its result. Fixing that, we have this code.
```python
#!/usr/bin/env python3
from binascii import unhexlify as u

def get_flag():
    flag = '666c61677b30682d6c6f6f6b2d612d466c61477d'
    return u(flag).decode('utf-8')

print(get_flag())
```

Flag: ```flag{0h-look-a-FlaG}```

---

# Reverse Engineering
## Luciafer's Cryptoware IOC 2 - 10 points

Luciafer's cryptoware causes even more ruckus by encrypting the victim's file names. Decrypt the filename and enter it as the flag: Example `flag{important-document.ext}`.

### Writeup

This challenge is more of a crypto than a rev. The file name, ```fkduohv-d-jhvfklfnwhu-wr-gdun-dqjho-01.oodev``` is encoded with a Caesar cipher of shift 3. 

Flag: ```flag{charles-a-geschickter-to-dark-angel-01.llabs}```

## TheZeal0t's Fingerprints Are All Over This! - 10 points
A "hash" is a "digital fingerprint" of a file that is astronomically improbable to duplicate with other content by accident, and nearly impossible to duplicate intentionally. Therefore, it is often used as a "shorthand" to identify a file.

Calculate the SHA256 sum of TheZeal0t's cryptoware program, and its decryptor program. Enter the two hashes as the flag, separated by a pipe symbol, with the cryptoware's hash first, followed by the decryptor program's hash. Example:

`flag{435524cc4113668d3f1e1e761d1717ba1bcf8b86b6dfaab9d048338e4e00a764|5d213aa47efd7e255c8304f56f148f87488a4bd9488f631ac4ed87f02c85cdce}`

### Writeup
We can find the SHA256 sum using this [online tool](https://emn178.github.io/online-tools/sha256_checksum.html).

Flag: ```flag{5a54fb61f7b1a9b1b7405602388add7e3323890bc74952a62803ffb1a535338b|969102c7feb6003624c4caf0e00fa9a60d96bc503ef0beb71ed4af68ba1fc047}```

---
# SQL
## Body Count - 10 points
One of our employees, Jimmie Castora, kept database backups on his computer. DEADFACE compromised his computer and leaked a portion of the database. Can you figure out how many customers are in the database? We want to get ahead of this and inform our customers of the breach.

Submit the flag as `flag{#}`. For example, _flag{12345}_.

Password: d34df4c3

### Writeup 

I used Visual Studio Code to view the SQL database dump. There we find a table named "customers" and in this table, there are customer IDs, names, emails, addresses, gender, and birthdates. Looking at the customer IDs, we see that the last ID number is 10000.

Flag: ```flag{10000}```

## Keys - 20 points
One of De Monne's database engineers is having issues rebuilding the production database. He wants to know the name of one of the foreign keys on the `loans` database table. Submit one foreign key name as the flag: `flag{foreign-key-name}` (can be ANY foreign key).

Use the MySQL database dump from **Body Count**.

### Writeup 
We find our "loans" table. 
```SQL
CREATE TABLE `loans` (
`loan_id` smallint NOT NULL AUTO_INCREMENT,
`cust_id` smallint NOT NULL,
`employee_id` smallint NOT NULL,
`amt` decimal(10,2) NOT NULL,
`balance` decimal(10,2) NOT NULL,
`interest` decimal(10,2) DEFAULT NULL,
`loan_type_id` smallint NOT NULL,
PRIMARY KEY (`loan_id`),
KEY `fk_loans_cust_id` (`cust_id`),
KEY `fk_loans_employee_id` (`employee_id`),
KEY `fk_loans_loan_type_id` (`loan_type_id`),
CONSTRAINT `fk_loans_cust_id` FOREIGN KEY (`cust_id`) REFERENCES `customers` (`cust_id`) ON DELETE CASCADE,
CONSTRAINT `fk_loans_employee_id` FOREIGN KEY (`employee_id`) REFERENCES `employees` (`employee_id`) ON DELETE CASCADE,
CONSTRAINT `fk_loans_loan_type_id` FOREIGN KEY (`loan_type_id`) REFERENCES `loan_types` (`loan_type_id`) ON DELETE CASCADE
```

The foreign keys are quite obvious. They are ```fk_loans_cust_id```, ```fk_loans_employee_id```, and ```fk_loans_loan_type_id```. 

Flag: ```flag{fk_loans_cust_id}```

## Address Book - 30 points
It looks like DEADFACE is targeting one of De Monne's customers. Check out this thread in Ghost Town and submit the customer's name as the flag: `flag{Jane Doe}`.

Use the MySQL database dump from **Body Count**.

[Ghost Town thread](https://ghosttown.deadface.io/t/why-do-people-fall-for-this/62)

### Writeup
In the thread, we see that the customer is female and lives in Vienna. CTRL+F-ing "Vienna" in the customer table yields 6 results.
1. Gronav, Rogers (Male)
2. Gummer, Kyle (Male)
3. Allsopp, Collen (Female)
4. Loade, Courtney (Male)
5. Brasier, Berke (Male)
6. Laguerre, Kimble (Male)

With the exception of Collen Allsopp, the other customers are all male. Thus, we have our target.

Flag: ```flag{Collen Allsopp}```

## City Lights - 40 points
De Monne wants to know how many branch offices were included in the database leak. This can be found by figuring out how many unique cities the employees live in. Submit the flag as `flag{#}`.

Use the MySQL database dump from **Body Count**.

### Writeup
First, we find our "employees" table.
```SQL
CREATE TABLE `employees` (
`employee_id` smallint NOT NULL AUTO_INCREMENT,
`last_name` tinytext NOT NULL,
`first_name` tinytext NOT NULL,
`email` tinytext NOT NULL,
`street` tinytext NOT NULL,
`city` tinytext NOT NULL,
`state` tinytext NOT NULL,
`country` tinytext NOT NULL,
`postal` tinytext NOT NULL,
`gender` tinytext NOT NULL,
`employee_code` tinytext NOT NULL,
PRIMARY KEY (`employee_id`)
```

Below this, we have our data from 4823 employees. We store all data in a text file. 

Now, we need to code a program to find all the cities. First, we have to pick out the cities in our data and compile them into a list.

```python
info = open('info.txt', 'r').read()
cities = [] # list of cities
employees = info.split('(') # isolate each employee
for i in range(1, 4823): # 4823 employees
    employee = employees[i].split(',') # split each employee data
    cities.append(employee[5]) # the 6th item of the list is the city
```

Then, we have to remove duplicate cities. 

```python
cities2 = [] # 2nd list of cities
for city in cities:
    if city not in cities2: # if the city is not in the list, add it
        cities2.append(city)
print(cities2) # prints all the cities
print(len(cities2)) # prints the total number of unique cities
```

Running our code altogether, we get 444.

Flag: ```flag{444}```

---
# Steganography
## Send in the Clowns - 10 points
There is a secret hidden somewhere in this image. Can you find it? Submit the flag as `flag{this-is-the-flag}`.

### Writeup
Using strings, we can get the flag.
Command: ```strings clown.jpg | grep flag```

Flag: ```flag{s3nd_in_the_kl0wns}```

## Scary Bunny - 10 points
What could be inside this creepy rabbit?

### Writeup
Using this [website](https://futureboy.us/stegano/decinput.html), we get our flag.

Flag: ```flag{Carr0t}```

## Behind the Curtain - 30 points
This image was intercepted from [Ghost Town](https://ghosttown.deadface.io/t/listen-up-noobs/43/4). We think Donnell has hidden information here, but there doesn't seem to be anything special about the image. Can you help find the hidden information? Submit the flag as `flag{this-is-the-flag}`.

### Writeup
Using binwalk, we can extract the files inside the photo.
Command: ```binwalk -e curtain.jpg```

Flag: ```flag{L3t_m3_in}```

## Voice - 50 points
A friend of mine sent me an audio file which supposes to tell me the time of our night out meeting, but I can't comprehend the voice in the audio file. Can you help me figure it out? I want to hang out with my friends.

### Writeup
Opening the audio file with Audacity and viewing it in Spectrogram mode, we see our flag. 

Flag: ```flag{1257}```

---

