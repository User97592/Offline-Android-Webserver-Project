# Offline Android Webserver Project

> I used generative AI to help me create this project documentation. The ideas and project presented here are my own.
>
> *My own personal commentary will be italicized.*

## 1. Project Overview & Objective

**Goal:** Host and run a static website (5e.tools) locally and entirely offline on an Android mobile device.

**Hardware:** Moto G Power (2021)

**Software/Tools:**
- Termux (Terminal emulator & Linux environment for Android)
- Lightweight web server (e.g., Python http.server, Nginx, or Node.js)
- LocalSend
- Personal PC with Linux Mint 22.3

### Quick Start Steps

1. Set up Termux so I can run bash scripts on my Android phone
2. Get the website (5e.tools) files downloaded onto my phone and unzip them
3. Make a bash script in Termux that finds the files and turns them into a website
4. Use my browser to visit the website I just set up
5. Document it all!
6. Enjoy my brand-new personal website

> *I already did this project once with a moto e5 play, a much weaker phone from 2018. However, that was a long time ago, and that phone mysteriously stopped rebooting sometime in September 2026.*
>
> *Also, 5e.tools is a very cool website for anyone who plays D&D 5e! Make sure to use an adblocker if you visit, or host it yourself like I do!*

## 2. Prerequisites & Setup

### Installing and Updating Termux

Termux is a program that lets me use a bash shell on an Android phone. Bash is the text language that Linux uses, so Termux essentially lets me use my Android phone like a mini Linux computer.

I already had Termux installed on this phone from a previous project. All I needed to do to make sure it's up-to-date is to run:

```bash
pkg update
