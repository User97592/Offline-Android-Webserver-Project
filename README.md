I used generative AI to help me create this project documentation.

*My own personal commentary will be italicized.*


1. Project Overview & Objective

    Goal: Host and run a static website (5e.tools) locally and entirely offline on an Android mobile device.

    Hardware: Moto G Power (2021)

    Software/Tools:

        Termux (Terminal emulator & Linux environment for Android)

        Lightweight web server (e.g., Python http.server, Nginx, or Node.js)

        Static site mirror/download tools

*I already did this project once with a moto e5 play, a much weaker phone from 2018. However, that was a long time ago, and that phone mysteriously stopped rebooting sometime in September 2026. So, to refresh my memory and to have a working version, I'm going to do it again!*


2. Prerequisites & Setup

    Preparing the Moto G Power:

        Installing and updating Termux.
        I already have Termux installed on this phone from a previous project. All I needed to do to make sure it's up-to-date is to run the command "pkg update".
        Termux uses pkg as its package manager, unlike other versions of Linux/bash that use snap, apt, yum and others.


        Granting necessary storage permissions (termux-setup-storage).
        eeee

        Installing required packages (e.g., Python, wget, git, etc.).

4. Acquiring and Preparing the Website

    Downloading 5e.tools:

        Method used to mirror or download the static site files.

        Structuring the directory layout for mobile storage.

5. Configuring the Web Server

    Setting up Termux:

        Navigating to the website directory.

        Launching the local server command.

        Binding to localhost (127.0.0.1) on a specified port.

6. Accessing and Testing

    Browsing Offline:

        Opening the mobile browser (Chrome/Firefox).

        Navigating to http://localhost:[port].

        Verifying offline functionality (ensuring assets, CSS, and data load correctly without an internet connection).

7. Challenges & Solutions (Optional / Troubleshooting)

    Note any hurdles faced (e.g., storage limits, background process management with Termux wake locks, relative path issues) and how you resolved them.

8. Conclusion

    Summary of the project's success and potential future enhancements (e.g., automation scripts, startup shortcuts).
