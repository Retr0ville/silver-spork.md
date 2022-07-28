---
title: Setting up NodeJS
tags: android blog rtrvl
author: retr0ville
source: 
---
Ever been in a position where you are without your laptop? (*or it died on you unexpectedly for some arcane reason*), while you were in the middle of squashing a ladybug that wouldn't let users successfully sign up on your top of the line website.
>No?
Well okay I admit that was a little too specific. Anyways here's how to use your phone **by which I mean Android** to spin up a fully functional nodeJS environment for all your on the go Server maintenance needs /s.
**First** you would want to 
### Download and Install the Termux app. 🧊
You would find a *version* on the Play store but I wouldn't recommend using that as it is outdated, unmaintained and possibly deprecated, so just head over to the official [GitHub Repo here](https://github.com/termux/termux-app/releases/tag/v0.118.0) and download the latest version *0.118.0* at the time of writing.
Or if you got beef with Microsoft you can as well get the latest version from [Fdroid](https://f-droid.org/en/packages/com.termux/), a great Open source application hosting site for Android.
Okay so what is Termux exactly? You may ask.
Well as the name would imply Termux is a ***Terminal emulator and Linux environment that runs on [Android's Linux kernel ](https://www.computerworld.com/article/2741578/are-android-and-linux-the-same-thing-.html).*** 
Termux combines powerful terminal emulation with an extensive Linux package collection.
With Termux you can:
• Enjoy the bash and zsh shells.
• Manage files with nnn and edit them with nano, vim or emacs.
• Access servers over ssh.
• Develop in C with clang, make and gdb.
• Use the python console as a pocket calculator.
• Check out projects with git.
• Run text-based games with frotz.
And much more... But let's get back to certain time here. We just want a simple nodeJS application.

Next step would be..
### Launching the App 
No brainer, press on it 👀

You would be greeted with a black screen much like, if not exactly like this
![](Screenshot_20220728-213834_Termux~2.png)
Looks familiar? Ofc it does. It's textbook terminal output.

Now let's see if it's functional,
I have tried out some simple Linux Commands like mkdir, ls, cd and cat
![](Screenshot_20220728-214739_Termux~2.png)
You will notice I already have some fully fledged applications in that directory, this is because I have previously installed Git and used it to pull a repository from my remote to work on with my phone.  For you it's all most likely a blob of emptiness. That's normal, and should be expected.

>Okay that's cool and all, but how do I actually install Node You may ask. We are getting there.
### So Thirdly
As you may have seen from my previous screenshot, Termux's package install command goes a bit like
`pkg install <package-name>`
 And another useful command also on the image is
 `pkg search <package-name>`
 And yes it does what you think it does.
#### Using the search command we can check to see if our package manager even has this thing called Node.
To do that we would.. you guessed it, do a search with 
`pkg search node`
This returns
![](Screenshot_20220728-220601_Termux~2.png)
And we can see that they have the Node v16 and
