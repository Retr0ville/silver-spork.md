---
title: 📇How to Make a Button With Awesome Hover Effects 02 | HTML & CSS✨ - DEV Community
tags: dev-to blog rtrvl
author: retr0ville
source: https://dev.to/robsonmuniz16/how-to-make-a-button-with-awesome-hover-effects-02-html-css-3m2e
---
📇How to Make a Button With Awesome Hover Effects 02 \| HTML \& CSS✨ - DEV Community  
Skip to content  
Navigation menu ![DEV Community](https://dev-to-uploads.s3.amazonaws.com/uploads/logos/resized_logo_UQww2soKuUsjaOGNB38o.png)  

DEV Community
-------------

DEV Community is a community of 886,185 amazing developers
----------------------------------------------------------
Robson Muniz

Posted on Aug 4

📇How to Make a Button With Awesome Hover Effects 02 \| HTML \& CSS✨
====================================================================

#html #css #beginners #webdev  
**How to Make a Button With Awesome Hover Effects 02 Using HTML \& CSS, step-by-step from scratch.**

**Source Code:**

**Markup:**   

    <!DOCTYPE html>
    <html lang="en">

    <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Button with Awesome Hover Effects</title>
      <link rel="stylesheet" href="style.css">
    </head>

    <body>
      <a href="#" class="green"><span>Button</span><i></i></a>
      <a href="#" class="blue"><span>Button</span><i></i></a>
      <a href="#" class="red"><span>Button</span><i></i></a>
    </body>

    </html>
Enter fullscreen mode Exit fullscreen mode

**Style:**   

    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: "Poppins", sans-serif;
    }

    body {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        background-color: #27282c;
        flex-direction: column;
        gap: 60px;
    }

    /* Colors */
    .blue {
        --clr: #2979ff;
    }
    .green {
        --clr: #00c853;
    }
    .red {
        --clr: #f50057;
    }

    a {
        position: relative;
        background-color: #444;
        color: #fff;
        text-decoration: none;
        text-transform: uppercase;
        font-size: 1.5em;
        letter-spacing: 0.1em;
        padding: 10px 30px;
        border-radius: 2px;
        transition: all .5s ease;
    }
    a:hover {
        letter-spacing: 0.25em;
        background-color: var(--clr);
        color: var(--clr);
        box-shadow: 0 0 35px var(--clr);
    }

    a::before {
        content: '';
        position: absolute;
        inset: 2px;
        background-color: #27282c;
    }

    a span {
        position: relative;
        z-index: 1;
    }

    a i {
        position: absolute;
        inset: 0;
        display: block;
    }
    a i::before {
        content: '';
        position: absolute;
        border: 2px solid var(--clr);
        top: -3.5px;
        width: 10px;
        height: 5px;
        left: 80%;
        border-radius: 2px;
        background-color: #27282c;
        transition: all .5s ease;
    }

    a:hover i::before {
        width: 20px;
        left: 20%;
    }

    a i::after {
        content: '';
        position: absolute;
        border: 2px solid var(--clr);
        bottom: -3.5px;
        width: 10px;
        height: 5px;
        left: 20%;
        border-radius: 2px;
        background-color: #27282c;
        transition: all .5s ease;
    }

    a:hover i::after {
        width: 20px;
        left: 80%;
    }
Enter fullscreen mode Exit fullscreen mode

🛴 **Follow me for more on:**   
YouTube: <https://bit.ly/3oBQbc0>  
Facebook: <https://bit.ly/3cp2S5W>  
Instagram: <https://bit.ly/3Ihh2EB>

Discussion (0)
--------------

Subscribe  
![pic](https://res.cloudinary.com/practicaldev/image/fetch/s--RmY55OKL--/c_limit,f_auto,fl_progressive,q_auto,w_256/https://practicaldev-herokuapp-com.freetls.fastly.net/assets/devlogo-pwa-512.png)  
Personal Trusted User ![loading](https://dev.to/assets/loading-ellipsis-b714cf681fd66c853ff6f03dd161b77aa3c80e03cdc06f478b695f42770421e9.svg)  
Create template

Templates let you quickly answer FAQs or store snippets for re-use.  
Submit Preview Dismiss  
Code of Conduct • Report abuse  
Are you sure you want to hide this comment? It will become hidden in your post, but will still be visible via the comment's permalink.

Hide child comments as well

Confirm

For further actions, you may consider blocking this person and/or reporting abuse

Read next
---------


![roodrigoomendes profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--k8jAJBuI--/c_imagga_scale,f_auto,fl_progressive,h_100,q_auto,w_100/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/891094/d438acf9-9191-4488-a040-914f316f34a7.jpg)  

### Top 3 Aplicativos para programar usando o celular

Rodrigo Mendes - Jul 13

![domiii profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--sdryqmX8--/c_imagga_scale,f_auto,fl_progressive,h_100,q_auto,w_100/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/143932/28c743e4-e889-4c59-b2bd-80a7f0a29ef4.png)  

### Making React less stupid: automatic \`useMemo\` and \`useCallback\` insertions are coming!

Domi - Jul 26

![jordantwells42 profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--hWER02qj--/c_imagga_scale,f_auto,fl_progressive,h_100,q_auto,w_100/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/893092/50757cd1-d0aa-41f9-a4c3-c0e63984a78a.jpeg)  

### I Made an Automatic Color Theme Generator for Tailwind CSS

Jordan Wells - Jul 17

![atulcodex profile image](https://res.cloudinary.com/practicaldev/image/fetch/s--TYpXVsLg--/c_imagga_scale,f_auto,fl_progressive,h_100,q_auto,w_100/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/164389/6308e2c2-b077-40cc-adc8-e77077a124f2.jpg)  

### Number countdown with html css \& javascript

Atul Prajapati - Jul 17  
![](https://res.cloudinary.com/practicaldev/image/fetch/s--gutzY-y5--/c_fill,f_auto,fl_progressive,h_90,q_auto,w_90/https://dev-to-uploads.s3.amazonaws.com/uploads/user/profile_image/543933/ff457294-8a9e-4ff7-b92b-ef7a28cf7cf4.jpeg) Robson Muniz  
Follow  
  * Joined  
Dec 20, 2020  

### More from Robson Muniz

Using GitHub with Visual Studio Code - The Easy Way!  
#webdev #beginners #github #git How to Create Amazing Buttons With Icons using HTML \& CSS  
#beginners #html #css #tutorial Input Label Animation \| HTML \& CSS  
#html #css #beginners  
Once suspended, robsonmuniz16 will not be able to comment or publish posts until their suspension is removed.  
Note:

Submit \& Suspend  
Once unsuspended, robsonmuniz16 will be able to comment and publish posts again.  
Note:

Submit \& Unsuspend  
Once unpublished, all posts by robsonmuniz16 will become hidden and only accessible to themselves.

If robsonmuniz16 is not suspended, they can still re-publish their posts from their dashboard.  
Unpublish all posts  
Once unpublished, this post will become invisible to the public and only accessible to Robson Muniz.

They can still re-publish the post if they are not suspended.  
Unpublish post  
Thanks for keeping DEV Community safe. Here is what you can do to flag robsonmuniz16:  
Make all posts by robsonmuniz16 less visible

robsonmuniz16 consistently posts content that violates DEV Community's code of conduct because it is harassing, offensive or spammy.  
Report other inappropriate conduct  
Confirm Flag  
Unflagging robsonmuniz16 will restore default visibility to their posts.  
Confirm Unflag  
DEV Community --- A constructive and inclusive social network for software developers. With you every step of your journey.  
Built on [Forem](https://www.forem.com) --- the [open source](https://dev.to/t/opensource) software that powers [DEV](https://dev.to) and other inclusive communities.

Made with love and [Ruby on Rails](https://dev.to/t/rails). DEV Community © 2016 - 2022.
[Forem logo](https://www.forem.com)  
![DEV Community](https://res.cloudinary.com/practicaldev/image/fetch/s--pcSkTMZL--/c_limit,f_auto,fl_progressive,q_80,w_190/https://practicaldev-herokuapp-com.freetls.fastly.net/assets/devlogo-pwa-512.png)  
We're a place where coders share, stay up-to-date and grow their careers.  
Log in Create account  
