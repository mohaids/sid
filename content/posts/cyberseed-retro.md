+++
date = '2025-03-09T18:54:21-04:00'
draft = false
title = 'UCONN CyberSEED 2025 Retrospective'
summary = "Couple of insights from the CTF"
ShowToc = true
tags = ["🏆 competition"]
[cover]
image = "/rpi-cyberseed.jpg"
alt = "ctf team image"
relative = false
+++

# Introduction
7 grueling hours. From 10 AM to 5 PM on the last Saturday before the end of my Spring break, I spent trying to solve the "Forensic & Log Analysis" and "Network Traffic Analysis" sections of the 2025 CyberSEED CTF competition. In this time period, I was either hunched, staring into my computer screen or pacing around, stressed out of my mind.

### Forensic & Log Analysis:
If I had to pick a favorite section, this would be my SECOND favorite. Nothing can beat the fun of OSI. Anyway, this section was pretty fun as well. In the end, I got 95.8% completion (with a 77.4% accuracy 💀). The 'Hard' problem was pretty fun - I was given a custom file format, and a description of how the file was formatted (eg. how many bytes were each 'section'). This was the most fun I'd had on a ctf problem as I first thought of giving up since the file was extremely long and I didn't want to spend my time grueling over trying to solve a complex question, such as which log entry transferred over the most bytes. Since this is the age of AI, I used it to first transcribe what the hex were as I wasn't able to simple copy paste them to a new txt file 😭. After I got the clean version of only the hex values I needed from the file, I could use the very same AI to analyze the clean verison of the hex and give me very accurate answers.

### Network Traffic Analysis 🤮
Dread it, run from it, NAT still arrives.

I tried doing my best on this section, but I could only complete 1.5 out of 4 problems. I clearly need to get more practice / become more familiar with Wireshark.

### OSI
My favorite section, by far. One challenge was a simple reverse image search, but it took me a little bit as it was an obscure image and there were numerous red-herrings. Another one was questions regarding a file, which I later found out to be a virus. I used Virustotal.com, but it seems like Malware Bazaar is the preferred site for this challenge. The final challenge I tried working on was something related to dig, but I was having trouble understanding it, so that an area to work on for next time.

### Takeaway
Highly recommend it. While at times I wanted to pull my hair out, I really had a lot of fun doing these challenges. I learned what some of my weak points are and am sure to beef up on those topics in preparation for other NCL competitions.