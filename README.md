I used generative AI to help me create this project documentation. The ideas and project presented here are my own.

*My own personal commentary will be italicized.*


****1. Project Overview & Objective****

    Goal: Host and run a static website (5e.tools) locally and entirely offline on an Android mobile device.

    Hardware: Moto G Power (2021)

    Software/Tools:

        Termux (Terminal emulator & Linux environment for Android)

        Lightweight web server (e.g., Python http.server, Nginx, or Node.js)

        LocalSend

        Personal PC with Linux Mint 22.3

*I already did this project once with a moto e5 play, a much weaker phone from 2018. However, that was a long time ago, and that phone mysteriously stopped rebooting sometime in September 2026. So, to refresh my memory and to have a working version, I'm going to do it again!*

*Also, 5e.tools is a very cool website for anyone who plays D&D 5e! Make sure to use an adblocker if you visit, or host it yourself like I do!*


****2. Prerequisites & Setup****

Preparing the Moto G Power:
   Installing and updating Termux.
        Termux is a program that lets me use a bash shell on an Android phone. Bash is the text language that Linux uses, so Termux essentially lets me use my
        Android phone like a mini Linux computer.
        I already have Termux installed on this phone from a previous project. All I needed to do to make sure it's up-to-date is to run the command "pkg update".
        Termux uses pkg as its package manager, unlike other versions of Linux/bash that use snap, apt, yum and others.

*If you want Termux on your Android phone, don't get it from the Google Play Store. I made that mistake. The version of Termux on the Google Play Store is very outdated. If you want a usable version, get it from F-Droid instead! It's a community-maintained app store for free and open-source apps. Also, it's under existential danger! If you want to learn more, check out websites like https://f-droid.org/ and https://keepandroidopen.org/*

        Granting necessary storage permissions (termux-setup-storage).
        This is important for a couple reasons. Mainly, it lets Termux interact with my phone's normal storage systems. This helps prevent my entire project from getting deleted when I close Termux. Finally, the website I'm going to download has hundreds of tiny files, and letting my phone handle all that instead of Termux itself is a very good thing.
        eeee


****3. Acquiring and Preparing the Website****

    Downloading 5e.tools:
Now we run into a limitation of the phone. Its CPU isn't very strong. So if I try to download the website (5e.tools) the phone could very well crash.
However,
Remember how I mentioned I did this before?
I already have the website files in my personal PC.
I can send the files from the PC to my phone using an app called LocalSend. It uses Bluetooth to transfer files locally (not going outside my home WiFi network). 

    Accessing 5e.tools files:
I've got the files now. The next step is making sure I can access it from Termux.
I know Termux can access my Downloads folder. I also know that there's all kinds of stuff in there, like the Kinderlumper song from Phineas and Ferb. So I'm going to make a folder inside Downloads and call it "5etools". That way it won't be hard to find what I'm looking for.
My phone's Files app can see all the files, but Termux just lists it as one zip file. I need Termux to see everything in the zip file, so I need to unzip it inside Termux. This requires a command called "unzip". I know, very creative name. Termux doesn't have it by default, so I'll run the install command to see if I installed it before.
I got the result "0 upgraded, 0 newly installed, 0 to remove and 71 not upgraded" when I told Termux to install unzip. That means that nothing changed, which means that I already have unzip installed. Nice.
Now to unzip the files. I'll let you know how it goes, dear reader.
I'm seeing a lot of audio files. I don't remember audio files in this website. But every file in the website is now flashing across my phone screen, which means it's all working.

*It's worth noting that I don't have the most recent version of 5etools on hand. I have v2.28.1, and the current version is 2.36.something.*

****4. Configuring the Web Server****

    Setting up Termux:

        Navigating to the website directory.

        Launching the local server command.

        Binding to localhost (127.0.0.1) on a specified port.

****5. Accessing and Testing****

    Browsing Offline:

        Opening the mobile browser (Chrome/Firefox).

        Navigating to http://localhost:[port].

        Verifying offline functionality (ensuring assets, CSS, and data load correctly without an internet connection).

****6. Challenges & Solutions (Optional / Troubleshooting)****

    Note any hurdles faced (e.g., storage limits, background process management with Termux wake locks, relative path issues) and how you resolved them.

****7. Conclusion****

    Summary of the project's success and potential future enhancements (e.g., automation scripts, startup shortcuts).
