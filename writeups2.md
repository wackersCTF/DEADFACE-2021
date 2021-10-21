# Writeups for Challenges Solved after Competition

## Programming: The Count - 275 points

Apparently DEADFACE is recruiting programmers, but spookyboi is a little apprehensive about recruiting amateurs. He's placed a password hash in the form of a flag for those able to solve his challenge. Solve the challenge and submit the flag as `flag{SHA256_hash}`.

[Link to Thread](https://ghosttown.deadface.io/t/what-programming-needs-are-there/56/4)

`code.deadface.io:50000`

### Writeup
We can connect to the challenge using netcat.
Command: ```nc code.deadface.io 50000```

After connecting, we get this:
```
DEADFACE gatekeeper: Let us see how good your programming skills are.
If a = 0, b = 1, c = 2, etc.. Tell me what the sum of this word is:

 You have 5 seconds to give me an answer.

Your word is: swift
Too slow!! Word has been reset!
^C
kylepak@yeti ~ % nc code.deadface.io 50000
DEADFACE gatekeeper: Let us see how good your programming skills are.
If a = 0, b = 1, c = 2, etc.. Tell me what the sum of this word is:

 You have 5 seconds to give me an answer.

Your word is: mix
```

We can write a script that connects to the challenge and automatically submits the answer, however I just ran a script in another terminal and submitted the answer within 5 seconds. 

Script:
```python
alphabet = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']
word = list(input())
summ = 0
for letter in word:
	summ += alphabet.index(letter)
print(summ)
```
For the word "mix" the sum of the word is 43. Submitting 43 gives us our flag.

Flag: ```flag{d1c037808d23acd0dc0e3b897f344571ddce4b294e742b434888b3d9f69d9944}```
