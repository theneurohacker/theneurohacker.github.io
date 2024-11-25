---
title: "Cicada-3301 TryHackMe Writeup"
date: 2024-24-11
draft: false
hideToc: true
tags: ["writeup", "osint", "steganography"]
---

![exiftool](https://miro.medium.com/v2/resize:fit:600/format:webp/0*ZEeS6uUHrkdcu_bc.jpeg)

In this room, we uncover hidden messages through steganographic methods and research.

---

## Task 2: Analyze the Audio
### Question: What is the link inside of the audio?
To solve this task, I used Sonic Visualizer to analyze the attached WAV file for hidden messages.
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*CjpKMpxru5Ce1zOpgyOeqg.png)
I added a new spectrogram layer and zoomed in to reveal a QR code. 
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*gpKAKt4PT-JzwfkDoc-4-A.png)
Scanning this QR code reveals a Pastebin link which is the answer for this task. Clicking on this link opens a text document with a passphrase and key. This information will be needed for the next task.
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*HjtkFiKi6qoO8roh2XSOPw.png)
### Answer: https://pastebin.com/wphPq0Aa

### Task 3: Decode the Passphrase
Find and Decrypt the passphrase and key
To decrypt the passphrase and key, I needed to identify the cryptographic methods used. I used a online hash identifier tool to reveal that both strings were base64. CyberChef can be used to decode them.
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*0A9SytAG1_x6fELcNV2TKw.png)
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*OIFKZOrgBOEvcJci83GMiA.png)
### Question: What is the decrypted passphrase?
### Answer: Hm5R_4_P455mhp453!
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*d2h7b5Ueo7pB6rsQjM8GuQ.png)
### Question: What is the decrypted key?
### Answer: Cicada

### Question: What is the final passphrase?
The hint in the room indicates that a French Diplomat Cipher is used, also known as the Vigenère cipher. CyberChef can be used to decode the Vigenère cipher.
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Hai2S2UPbNl4z52PO8xDrw.png)
However, this did not seem correct so I reencoded the passphrase to reveal the final passphrase.
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*1tKYUvlrvjoh_NB4GRoBog.png)

### Answer: Ju5T_4_P455phr453!
## Task 4: Gather Metadata
### Question: What link is given?
Steghide can be used to extract the hidden files with the passphrase found from the previous task. This resulted in an invitation.txt file, which contained an Imgur link. I downloaded the image from the link so it can be used in the next task.
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Af5OC6x_ISNHeazQAMjA6w.png)
### Answer: https://imgur.com/a/c0ZSZga
![exiftool](https://miro.medium.com/v2/resize:fit:1230/format:webp/1*h-KkdHtO1iE4DCILrv_N_w.png)
## Task 5: Find Hidden Files
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*LzWgIWtWjLLsAjADZXR4xw.png)
### Question: What tool did you use to find the hidden file?
To answer this question, I needed to identify the proper steganographic method. Initially I tried different methods that I was familiar with but had no success. The hint revealed that the method used was one originally relied upon in the real Cicada 3301 challenge. I searched up Cicada steganography tools to discover that Outguess was the method used. 
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*7YKlPTHiqPct8W0ZlQJkJQ.png)
(If outguess is not on your system, you can used 'apt install outguess' to install it.)
I ran this command to extract the hidden information contain within the jpg file
![exiftool](https://miro.medium.com/v2/resize:fit:1122/format:webp/1*_PtEzcn17sTaSfsy2HTFQg.png)
### Answer: Outguess
## Task 6: Book Cipher
The output file from Outguess revealed this secret message. 
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*4bpoOMGOM6RM3eAUKTK7bg.png)
### Question: What is the Hash type?
To crack the hash I first needed to identify its type. I used the same hash indentifier tool from earlier to do this (https://hashes.com/en/tools/hash_identifier)
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*QCDXndT7EaxNw3oM6h6HRA.png)
### Answer: SHA512
### Question: What is the Link from the hash?
This hash cannot be cracked with a offline tool, such as hashcat, and instead needed to be cracked with an online tool. I used (https://md5hashing.net/) to crack the hash and uncover the link for the answer.
![exiftool](https://miro.medium.com/v2/resize:fit:1096/format:webp/1*qnEljm7fHBrT6L2d0hZ_NA.png)
### Answer: https://pastebin.com/6FNiVLh5
Visiting this link reveals a long text file. This document is key to uncovering the link needed for the next question
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*jTwegAwx16aqOSiN8Y0x2A.png)
### Question: What is the link?
To decode the document, I used the message contained within the output file from earlier. The instructions stated that positive integers mean move forward in the sentence and negative integers mean to go backwards. The codes seemed to follow the format: (I:line number: character position). *Spaces are not included 
Following this format, I uncovered the link.
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*In6_JVMJzRLSsx8YnKfPdw.png)
### Answer: https://bit.ly/39pw2NH
## Task 7: The Final Song
### Question: What is the song linked?
I visited this link which led me to a SoundCloud page. The song title is the answer for the final task question. 
![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*KqA-tnQ9_UUvSE6-GlBf5A.png)
### Answer: The Instar Emergence