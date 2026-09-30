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

In short, here are the steps:
1. Set up Termux so I can run bash scripts on my Android phone
2. Get the website (5e.tools) files downloaded onto my phone and unzip them
3. Make a bash script in Termux that finds the files and turns them into a website
4. Use my browser to visit the website I just set up
5. Document it all!
6. Enjoy my brand-new personal website


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

*I'm seeing a lot of audio files. I don't remember audio files in this website. But every file in the website is now flashing across my phone screen, which means it's all working.*

Unzipping the files absolutely worked. We're in business, dear reader.

*It's worth noting that I don't have the most recent version of 5etools on hand. I have v2.28.1, and the current version is 2.36.something.*

****4. Configuring the Web Server****
We're nearly there.
All I need to do is tell Termux how to run the website. It already has all the stuff it needs, just not the instructions.
In order to do this, I'm going to do some light scripting.

*Scripting is different from programming. Scripting is chaining together a bunch of pre-existing commands in a file and then running that file. It's automation. Programming is about solving problems and making things with computer software and languages like python.*

Here's what the script is going to do:
- Tell bash (Termux) to run a webserver with my 5etools files

In order to make that happen:
- The script needs to know where the website files live.
- The script needs to go there and start a webserver in that folder.
- The script needs to assign an IP address that I can access from my phone's browser.

I'm going to write the script, put it in the /config folder, and then come back here. See you soon, dear reader!

The script is there now. It's all set up in Termux, and there's a copy in the config folder.
The thing is, the bash script as it is now is just a text file. Termux doesn't know that it's supposed to be read as instructions (executed). There is a quick fix to that in Linux/Termux. The command is "chmod +x (your file here)." "chmod" stands for "change mode", and the +x says to make it executable (readable as instructions).



****5. Accessing and Testing****

It should all be good to go. I have all the files. I have the script that runs the website. Termux knows it's a script.
I'm going to run the script now. All I need to enter into the command line is the file name and extension, so in my case it's "5etools.sh".

I had a strange issue where the settings/notifications dropdown menu kept getting pulled down and up again without me doing anything. I've had errors like these ever since I cracked both bottom corners of the screen in my local movie theater.
I'm going to restart my phone to hopefully fix this issue. I also had about seven apps open. Anything past three tends to make performance worse. Anyway, the home screen is back. Back into termux we go.

Using "ls" shows me the script, the storage folder, and a few other things that aren't relevant to today's project.

*The ls command lists everything in the folder you're inside. It's how we Linux nerds see what's in the folder without something like File Explorer or any graphics. You can use ls -l (list -long) to see a more detailed view. Try it at home, it's fun!*

Now, I'm going to check the nano file to make sure the script is still there. I did save and exit nano, but I restarted the phone with Termux still up. Hopefully nothing else is going wrong.
Also, the notification dropdown is fixed now.
The script looks good. Exactly as I left it.
I guess it's time to finally take this thing for a test run. Cue the Top Gear music!

I forgot: In order to execute the file in Termux you need to tell it which language it's using. For bash it's "bash (your file here)". You can do this with Python, too, using "python3 (your file here). Here I go, for realsies this time.

Looks like a success so far! It's telling me that it's "Serving HTTP on :: port 8080 (http://[::]:8080/) ...

*That monstrosity in the parintheses is the address, or the location where the website can be found acting as a website. It looks scary but it's just IPv6. I'm not going to get too far into IPv6 today, but you should know it does the same thing as an IP address like 192.168.0.10 or 127.0.0.1 (no place like home).*

I'm going to open up my browser of choice *(Firefox, obviously)* and go to the address to see if it works.




****6. Challenges & Solutions (Optional / Troubleshooting)****

A roadblock! Finally!
Firefox is saying that the website is unable to connect. I'm going to go investigate and report back to you, dear reader.

Turns out that monstrosity in the parintheses was the problem. In order to explain why, we're going to have to get into IPv6.
You may be familiar with IPv4. That's things like 192.168.0.1 (quite possibly your router's address) and 127.0.0.1. Remember that second address, 127.0.0.1. It gets important pretty soon.
**Wall of text incoming.** I researched IPv6 for this. You can skip ahead past the giant block to where I solve the problem if you want.

When IPv4 came out, it was really cool. It had a few billion possible addresses, because people thought that there would only be a few billion devices that needed to network with each other. However, they underestimated how many devices would be connecting to the Internet. They underestimated that number so severely that other people knew that there were going to be no more addresses very quickly. We officially ran out in 2011, about 30 years after IPv4 was invented, thanks to the ingenious inventions and life-saving work of hundreds of people trying to make the Internet support all the new devices that spawned between 1980 and 2011.
The solution was simple. We needed a new way of networking, and thus IPv6 was born. As for IPv5, we don't really talk about it. We had moved on to IPv6 immediately.

IPv6 fixes the problems IPv4 has in a few ways. Namely, each address is longer than IPv4's, and it uses base-16 instead of base-10. This resulted in IPv6 having 340 undecillion addresses, compared to IPv4's measly few billion. It's the same principle that explains why longer passwords are harder to crack. An IPv6 address will often look like "2001:0db8:0000:0000:0000:0000:1428:57ab". For context, an IPv4 address looks like "127.0.0.1".
Now, there's a special rule with IPv6 addresses. If there's a bunch of zeroes in a row, you can replace them with two colons (::). This is because our computers were pretty smart when IPv6 was invented, and they could remember how long the IPv6 address is supposed to be. Recall our good friend 2001:0db8:0000:0000:0000:0000:1428:57ab. Since there's sixteen zeroes in a row, we can shorten it to 2001:db8::1428:57ab. The thing to remember is, we can only do that once in an address, otherwise both you and your computer will have no idea how many zeroes should go in each spot.
The IPv6 address my script produced was just "::". That means that it's all zeroes. That's a special address in IPv6. Its equivalent in IPv4 is 0.0.0.0. If you direct something to ::, it tries to send its data all over the place. This is different from what we want. We want something called localhost, which is your device's internal IP address. It's great for things like my custom webserver. It's not at ::, it's at 127.0.0.1. Remember that address? I told you it's important.

Here's how we're going to fix our problem.

**I FIX THE IPV6 PROBLEM HERE**

Right now Termux is trying to make the website live at ::, which is basically 0.0.0.0. That's not good, and also doesn't work.

Also, Firefox on Android can be finicky about IPv6 addresses.

So, to fix this, we're going to tell the script what IP address to host the website on. In our case, it's our good friend 127.0.0.1, who likes to go by Localhost.

All we need to do is add a bit to the end of the script. The bit in question is "--bind 127.0.0.1". So before, the last line looked like:

    python3 -m http.server 8080

But now it will look like:

    python3 -m http.server 8080 --bind 127.0.0.1

This will force Termux to keep the website at Localhost, where the browser can see it.

Now, in theory, browser access should work. Here I go!
SUCCESS!!!

Firefox can now connect to our good friend Localhost!

Now, to test the connectivity. I should be able to see this website completely offline. To test this I'm going to turn on Airplane Mode.
It's on now. Now going to another webpage to force 5etools to load another set of files.

Success!

It works offline as well!

Finally, to make sure the website stops when I tell it to. I'm going to use bash's built-in stop command to stop the webserver while my browser is there. The command is Control+C. Then, I'm going to tell the website to send me back to its homepage, thus forcing it to load different files. In theory, it should give me an error like "Unable to Connect", since the webserver won't be up anymore.

Success again!

So we know the webserver works, lives in the right spot, and stops when I tell it to!

Overall, this project is a resounding success!

*You should imagine me wearing a top hat and monocle when I said "resounding success". It says it right here. You're required to do it. Mustache, gaudy accent and everything. There we go. A resounding success!*


****7. Conclusion****
Here's what I did in this project:
Environment Preparation & Maintenance:

    Updated and upgraded Termux package repositories (pkg update) to ensure a stable Linux environment on Android.

    Checked and configured Android shared storage permissions (termux-setup-storage) to seamlessly bridge mobile storage and Termux.

File Management & Unzipping:

    Transferred a large static website archive locally from a PC to the phone using LocalSend.

    Explored mobile storage paths (~/storage/shared/Download/) and utilized the unzip utility in Termux to extract thousands of static HTML, CSS, JavaScript, and JSON assets.

Web Server Configuration:

    Leveraged Python's lightweight built-in HTTP server (http.server) to act as a local web host without needing heavy infrastructure like Apache or Nginx.

    Solved local networking and binding quirks by explicitly forcing IPv4 localhost (--bind 127.0.0.1 on port 8080) to bypass mobile IPv6 resolution issues.

Automation & Scripting:

    Built a custom, reusable Bash automation script (5etools.sh) granting execution permissions (chmod +x), allowing the entire server stack to spin up instantly from the Termux home directory with a single command.

Testing:

    Successfully validated the offline deployment by browsing directly to [http://127.0.0.1:8080](http://127.0.0.1:8080) in a mobile browser.

