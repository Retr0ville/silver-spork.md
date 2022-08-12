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
  
