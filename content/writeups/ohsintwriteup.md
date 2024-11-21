---
title: "OhSINT TryhackMe Writeup"
date: 2024-20-11
draft: false
hideToc: true
tags: ["writeup, osint"]
---

![exiftool](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*SekVhAaN0ZLISUlsuo4ogw.jpeg)

This TryHackMe room demonstrates how easy it is to extract identifiable information from a single photo, showcasing the power of Open Source Intelligence.
## 1. What is this user’s avatar of?

For the first step, I used ExifTool to extract the metadata from the image file attached to the room. By examining this metadata, I found a username in the copyright field: OWoodflint.
![exiftool](https://miro.medium.com/v2/resize:fit:720/format:webp/1*VPhg69nhJpVIZRQ3SP36VQ.png)

I then searched Google for this username and discovered several platforms where this user has an account. The first result shows the user’s avatar.
![exiftool](https://miro.medium.com/v2/resize:fit:720/format:webp/1*VPhg69nhJpVIZRQ3SP36VQ.png)


### Answer: Cat
## 2. What city is this person in?

The answer to this question can be found in the GitHub result. Clicking on this repository link will reveal the user’s city.
![exiftool](https://miro.medium.com/v2/resize:fit:720/format:webp/1*tf9bkbzdrYa5i2FulGfW6A.png)


### Answer: London
## 3. What is the SSID of the WAP he connected to?

Going back to the X account, one of the posts contains the user’s BSSID which can be used to find their SSID
![exiftool](https://miro.medium.com/v2/resize:fit:720/format:webp/1*M2I4LpQBrNt504cZIcj-rg.png)


I entered the BSSID into Wigle.net and set the location to London which revealed the SSID

(You may need to sign up to use the search feature)
![exiftool](https://miro.medium.com/v2/resize:fit:720/format:webp/1*b1991qzCrdqZwucA7iyeHQ.png)

### Answer: UnileverWiFi
## 4. What is his personal email address?

The personal email address can be found in the GitHub repository discovered earlier.
![exiftool](https://miro.medium.com/v2/resize:fit:720/format:webp/1*O47oSsUmed4hfpMV6eKv0Q.png)


### Answer: OWoodflint@gmail.com
## 5. What site did you find his email address on?

### Answer: GitHub
## 6. Where has he gone on holiday?

To find out where he has gone on holiday, I checked the WordPress link in the GitHub Repository.
![exiftool](https://miro.medium.com/v2/resize:fit:720/format:webp/1*U2t444lGUIASonmeq94Xgg.png)


### Answer: New York
## 7. What is the person’s password?

The password can also be found on the WordPress page.
![exiftool](https://miro.medium.com/v2/resize:fit:640/format:webp/1*c1hGddVqwm7DIS3kFqZfBQ.png)


### Answer: pennYDr0pper.!