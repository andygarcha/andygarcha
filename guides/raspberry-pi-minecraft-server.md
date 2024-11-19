# Setting up a Raspberry Pi to work as a Minecraft Server
Hey all, I've done this process a few times at this point and have had to re-learn every time how to get it all installed the way I want to so I've decided to make this guide. Please enjoy!!

## Step 0: Purchasing materials
If you don't think more than 5 people are going to be on at a time, I would recommend sticking with the 4GB version. The Raspberry Pi 5 (8GB) was $70, while the Pi 5 (4GB) was only $50, which I believe was a marginal enough difference not to upgrade.

## Step 1: Unboxing and Setting Up the Raspberry Pi
When setting up your Raspberry Pi, you have a lot of options to make. Here's what you need to do specifically:
- Choose Raspberry Pi OS Lite (64-bit). This will increase the amount of memory you have access to (by using 64-bit addressing), and by choosing Lite, you remove a headless display and allocate more computing power and RAM to your server
- Make sure to put in your WiFi credentials. This saves you a lot of headache trying to connect to WiFi in a terminal menu.

## Step 1a: Connecting to WiFi (Georgia Tech specific)
You're gonna need the MAC address of the Pi to access the WiFi itself. It may come on the package, but you can also check by typing `ifconfig` and choosing the address under "wlan0". If you don't have a display, connect the Pi to another computer via ethernet and try it that way.

## Step 2: FreeMyIp
I use [FreeMyIp](https://freemyip.com) to allow my friends to connect to the server. While an IP address itself works, it's a) not very secure, and b) my WiFi provider does not give me a static IP, so things got very messy. Here's the steps to follow for this (or you can follow the instructions [here](https://freemyip.com/help) in case these steps are out of date:
1. Go to [freemyip.com](https://freemyip.com)
2. Type in your custom domain (make it unique!)
3. Claim it if it's available
4. SAVE THAT URL!!! You will need it in a minute, and if you navigate away from the page it will be lost forever.
5. Follow to the page it gives you marked "How do I use it?", or something along those lines
6. Scroll down until you see this message: <img width="1160" alt="Screenshot 2024-11-17 at 8 21 51 PM" src="https://github.com/user-attachments/assets/0a8ce25c-5dd8-48fd-9be7-ddccd9f332cf">
7. Copy the code underneath this message, and paste it into your Raspberry Pi Terminal
