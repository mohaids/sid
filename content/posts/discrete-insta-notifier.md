+++
date = '2025-05-04T11:59:16-04:00'
draft = false
title = 'Discrete Insta Notifier'
summary = "Using tampermonkey and discord webhooks to get insta notifications discretely"
ShowToc = true
tags = ["🎉 projects"]
[cover]
image = 
alt = "tampermonkey and discord cover image"
relative = false
+++

# Introduction
For one reason or the other, one might want to discretely get Instagram notifications, and one way you could go by doing that is getting an alert on your Discord if you get an Insta notification.

## Overview of this process flow:
For this proof-of-concept, you need to have the Instagram Direct Message (DM) tab running in the background. The purpose of [tampermonkey](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/) is to continuously monitor the DMs page and see if the tab's title changes as a result of a new DM. If it detects the change, it should call your personal Discord server's webhook to send a message.

Thus, you can discretely receive Instagram notifications via a Discord message - obviously not the actual content of the message, but that you received a message.

The only apparent downside to this whole process is that you have to keep the tab running in the background for this to work. 

### Materials needed:
1. personal Discord server
2. tampermonkey browser extension
    \- thus, you need to use a desktop browser

### Step 1: Set up your Discord webhook
Naviage to your personal server's settings, click on "Integration" on the left side column, click on "Webhooks", then finally click on "New Webhook".

Click on the newly created Webhook, here you can customize its name, icon, and channel. Most importantly make sure to copy / make note of its URL by clicking "Copy Webhook URL".

### Step 2: Install tampermonkey and load the script:
Personally I used Firefox, so I used this [link](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/) to add the extension. 

Find the extention and click on "Create a new script..."

Copy and paste the following script:
```javascript
// ==UserScript==
// @name         Instagram DM Alert
// @namespace    http://tampermonkey.net/
// @version      1.1
// @description  Alerts when Instagram tab title shows new DMs
// @match        https://www.instagram.com/*
// @grant        GM_xmlhttpRequest
// @connect      discord.com
// ==/UserScript==

(function() {
    'use strict';
    const discordWebhookURL = "https://discord.com/api/webhooks/custom-url";
    let lastTitle = document.title;
    let isSending = false; // Prevent duplicate sends

    console.log("Script loaded!");
    setInterval(() => {
        const currentTitle = document.title;
        console.log("Checking title:", currentTitle);

        if (/\(\d+\)/.test(currentTitle) && currentTitle !== lastTitle && !isSending) {
            console.log("DM detected! Sending to Discord...");
            isSending = true;

            GM_xmlhttpRequest({
                method: "POST",
                url: discordWebhookURL, // Direct Discord URL
                data: JSON.stringify({
                    content: "📬 New Instagram DM!",
                    flags: 4 // Makes notification ephemeral
                }),
                headers: {
                    "Content-Type": "application/json"
                },
                onload: function(response) {
                    console.log("Success! Status:", response.status);
                    lastTitle = currentTitle;
                    isSending = false;
                },
                onerror: function(error) {
                    console.error("Webhook error:", error);
                    isSending = false;
                }
            });
        }
    }, 15000); // 15 second interval to avoid rate limits
})();
```

Replace the `discordWebhookURL` variable with the Webhooks URL you copied.

Click `ctrl+s` to save the code.

### Step 3: Test the flow
To ensure that this flow works, ask your friend, or use an alt account to send your account a DM.


## Future Plans:
Current contraints:
1. Ideally you'd want to monitor just one user's DMs, but this script monitors all the DMs you get
    \- Use a more finecomb technique or continue to experiment if tampermonkey can solve this issue
2. This process requires you to have instagram.com running in the background
    \- Potential solution: utilize the cloud in some way?