**Platform**: TryHackMe | **Difficulty:** Easy | **OS:** Kali Linux  
**Tags:** `Cybersecurity` `TryHackMe` `CTF Writeup` `OSINT` `InfoSec`

![OhSINT Banner](banner.jpg)

Hi everyone! Today I’m sharing my walkthrough for the **OhSINT** room on TryHackMe. The challenge gives us just one image file and asks us to answer 7 questions using Open-Source Intelligence (OSINT) techniques.

First, I downloaded the task file onto Kali Linux and renamed it to **`img.jpg`** so my terminal commands would stay short, clean, and easy to type. Let’s get started!

---

### 1. What is this user's avatar of?

To inspect the image's hidden EXIF metadata, I ran `exiftool` in the Kali terminal:

```bash
exiftool img.jpg
# TryHackMe-OhSINT-Write-UpLooking through the output, the Copyright field gave away a username: OWoodflint.
​Searching "OWoodflint" in the browser immediately led me to the target's X (Twitter) profile (@OWoodflint), where we can clearly see their profile picture.
​Answer: cat

​2. What city is this person in?
​On that same X (Twitter) profile, there is a post sharing the BSSID of their home Wi-Fi: B4:5D:50:AA:86:41.
​By plugging that BSSID into WiGLE.net (a public database that maps wireless access points), we can pinpoint the exact physical location of the router—and we also see the same city confirmed later on their GitHub bio.
​Answer: London

​3.  What is the SSID of the WAP he connected to?
​Looking closely at the WiGLE.net map entry for B4:5D:50:AA:86:41 from the previous step, it also displays the wireless network's name (SSID).
​Answer: UnileverWiFi

​4. What is his personal email address?
​Next, I checked the target's GitHub account (OWoodfl1nt), which came up in our initial search results. Inside their people_finder repository, the README.md file openly lists their contact email.
​Answer: OWoodflint@gmail.com

​5. What site did you find his email address on?
​We pulled that email address directly from the README.md documentation on their public repository.
​Answer: GitHub

​6. Where has he gone on holiday?
​At the bottom of the GitHub README.md, there is a link to their personal WordPress blog (oliverwoodflint.wordpress.com). Opening the blog reveals a short post updating readers on their current trip.
​Answer: New York

​7. What is this person's password?
​Staying on the WordPress blog, I inspected the page source (or highlighted the blank space on the page) and spotted a hidden string disguised as white text on a white background—giving us the final flag!
​Answer: [********] (Kept blurred for good cybersecurity practice)


​Thanks for reading! If you're practicing OSINT on TryHackMe, this room is a great reminder of how much information a single photo's metadata and a few public posts can expose.