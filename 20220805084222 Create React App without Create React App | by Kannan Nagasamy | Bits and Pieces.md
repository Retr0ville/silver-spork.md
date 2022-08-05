---
title: Create React App without Create React App | by Kannan Nagasamy | Bits and Pieces
tags: android blog rtrvl
author: retr0ville
source: https://blog.bitsrc.io/create-react-app-without-create-react-app-b0a5806a92
---
Create React App without Create React App \| by Kannan Nagasamy \| Bits and Pieces  
[](https://medium.com/)  
[Open in app](https://rsci.app.link/?$canonical_url=https%3A%2F%2Fmedium.com/p/b0a5806a92&~feature=LoOpenInAppButton&~channel=ShowPostUnderCollection&~stage=mobileNavBar)  
[](https://medium.com/)  
[Home](https://medium.com/)
[Notifications](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fmedium.com%2Fme%2Fnotifications&source=--------------------------notifications_sidenav-----------) [Lists](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fmedium.com%2Fme%2Flists&source=--------------------------lists_sidenav-----------) [Stories](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fmedium.com%2Fme%2Fstories%2Fdrafts&source=--------------------------stories_sidenav-----------)  
[Write](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fmedium.com%2Fnew-story&source=--------------------------new_post_sidenav-----------)  
[![Bits and Pieces](https://miro.medium.com/fit/c/64/64/1*CbLVQCvVuulnBXlbu3B21A.png)](https://blog.bitsrc.io/?source=post_page-----b0a5806a92--------------------------------)  
Published in
[Bits and Pieces](https://blog.bitsrc.io/?source=post_page-----b0a5806a92--------------------------------)  
[![Kannan Nagasamy](https://miro.medium.com/fit/c/96/96/0*tZuggF3akejte824)](https://medium.com/@kannankannan18?source=post_page-----b0a5806a92--------------------------------)  
[Kannan Nagasamy](https://medium.com/@kannankannan18?source=post_page-----b0a5806a92--------------------------------)  
[Follow](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fsubscribe%2Fuser%2Fc6778e363b04&operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&user=Kannan+Nagasamy&userId=c6778e363b04&source=post_page-c6778e363b04----b0a5806a92---------------------follow_byline-----------)  
Feb 16  
·  
6 min read  
[](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fbookmark%2Fp%2Fb0a5806a92&operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&source=--------------------------bookmark_header-----------)  
[Save](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fbookmark%2Fp%2Fb0a5806a92&operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&source=--------------------------bookmark_header-----------)  

Create React App without Create React App
=========================================

![](https://miro.medium.com/max/1400/1*12Xgy-DmusIsxKVyJSZFOQ.png)

This article talks about the process of creating react app without using any libraries or frameworks such as "create-react-app" , "NextJS" etc.

Prerequisites concepts to know
------------------------------

* **Webpack ---**helps in bundling our code into one single file
* **Babel** --- used to convert ECMAScript 2015+ (ES6+) code into a backwards compatible version of JavaScript that can be run by older JavaScript engines.
* **Node.js** --- installing node, creating package.json and installing node modules using npm

This article will help us to understand
---------------------------------------

* How webpack and babel work in a more practical sense;
* The actual starting to ending flow of building the React app;
* How development and production build is being setup and its significance;
* Setting up the server details thats required;
* Writing webpack and babel config files and understanding the logic that exists there;
* How we can configure client-side and server-side rendering;
* Understanding how HMR is works in React.

Source code
-----------

* *Repository ---* [*https://github.com/kannanagasamy/react-app-without-cra*](https://github.com/kannanagasamy/react-app-without-cra)
* *Branch --- main*

Step by Step
============

1. Make sure node is installed in your system
---------------------------------------------

Install Node.js in your system and make sure its installed by typing `node -v` in your terminal.

2. Create project folder and package.json
-----------------------------------------

Create a project folder of any name and navigate to the folder and then use `npm init` to create a **package.json**file inside the folder. Navigate to the folder.

3. Install webpack dependencies
-------------------------------

```
npm i --save-dev webpack webpack-cli webpack-dev-server
```

* **webpack** --- Will allow us to bundle all of our code into a final build
* **webpack-cli ---**CLI tool for providing a flexible set of commands for developers to increase speed when setting up a custom webpack project. If you're using webpack v4 or later and want to call webpack from the command line, you need this
* **webpack-dev-server ---** Webpack dev server is a mini Node.js Express [server.It](http://server.It) uses a library called SockJS to emulate a web socket. Will enable us to create a localhost dev environment

4. Install the Babel dependencies
---------------------------------

```
npm i --save-dev babel-loader @babel/preset-env @babel/core 
@babel/plugin-transform-runtime 
@babel/preset-react 
babel-eslint 
@babel/runtime
@babel/cli
```

* **babel-loader ---**allows transpiling JavaScript files using babel and webpack. exposes a loader-builder utility that allows users to add custom handling of Babel's configuration for each file that it processes.
* **@babel/preset-env ---**allows you to use the latest JavaScript without needing to micromanage which syntax transforms (and optionally, browser polyfills) are needed by your target environment(s). This both makes your life easier and JavaScript bundles smaller!
* **@babel/core ---**core package
* **@babel/plugin-transform-runtime ---**A plugin that enables the re-use of Babel's injected helper code to save on codesize.
* **@babel/preset-react ---**use react preset when we are using Reactjs. Helps in converting html files to react based file
* **babel-eslint ---**parser that allows ESLint to run on source code that is transformed by Babel
* **@babel/runtime ---**package that contains a polyfill and many other things that Babel can reference.
* **@babel/cli ---**command line interface to use babel

5. Install required Linters and path
------------------------------------

```
npm i --save-dev eslint eslint-config-airbnb-base 
eslint-plugin-jest 
eslint-config-prettier
path
```

6. Install react and react-dom
------------------------------

```
npm i react react-dom
```

7. Create index.html file
-------------------------

Create folder called "**public"** in the root of the project. Inside that, create **index.html**.

8. Create App.js file
---------------------

Create src folder and inside that create a file called **App.js**. Add the following code to it:  

8. Create index.js file
-----------------------

Create an **index.js** file at the root of project or anywhere you wish to have. This will act as entry point for our webpack.

Add the following code to it:  

9. Create webpack.config.js file
--------------------------------

Create a file called **webpack.config.js** at the root of project and add the following code. On a higher note, this file contains configs that takes care of bundling the files into one single file and setting up the dev server.

The comments in the code helps us understand what each line does:  

10. Create .babelrc file
------------------------

Create a file called .babelrc at the root and add the following code.

This is the configuration file for Babel, and you'll use it to tell babel to use the plugin and presets defined inside.  

11. Update package.json file
----------------------------

Add the start and build scripts to it --- *line number 7 and 8.*

* The **start** script asks to run the webpack-dev-server in our current project at port 9500, from the public folder.
* The build command asks us to **build** this package in **main.js** file. It actually runs all logic in **webpack.config.js** file.

12. Final project folder structure has to be like this
------------------------------------------------------

![](https://miro.medium.com/max/1032/1*rKVs9s3qtTTuZc1tmJ3K8w.png)

13. Run "npm run build"
-----------------------

* Once added the above code, hit `npm run build`. it generates **main.js** file in our **public** folder. The file is actually **over 1 MB** in size. This is our development build.

14. Run "npm start"
-------------------

Start the application by giving `npm start` from terminal. This will start our dev server.

The final code can be found in the repo link I shared above.

Other Key Findings
==================

Changing the build to production
--------------------------------

* Now we can try changing it to production build. For this you need to make the following change to **webpack.config.js** file.

```
mode: "production"
```

* now running `npm run build` will create **main.js** file again but the size will be very less (\<200kb).
* With the optimization from **1000 KB** to **200 KB** , we might want to use production build always. But, we should use development mode while doing development because the **hot reloading is faster in development mode.**

Hot Module Replacement
----------------------

* HMR is handled by webpack-dev-server. We can use HMR without page load option too. Setting the required options helps greatly in performance aspect.
* Check the below code snippet for various scenarios:

```
//If you want to use HMR but no live reload then use the below config in webpack.config.js
devServer: {
        hot: true ,
        liveReload:false
    }

//If you want don't want to use HMR but want to use live reload then,
devServer: {
        hot: false ,
        liveReload: true
    },

//If you want don't want to use live reload then,
devServer: {
        hot: false , //this is mandatory to be set to false for this
        liveReload: false
    },
```

References
----------

1. HMR with webpack --- <https://webpack.js.org/guides/hot-module-replacement/>
2. Different ways to reduce the bundle size --- <https://blog.jakoblind.no/3-ways-to-reduce-webpack-bundle-size/>
3. Understanding devserver and working in details --- <https://webpack.js.org/configuration/dev-server/#devserverlivereload>
4. Minimizing the bundle for production --- <https://webpack.js.org/plugins/mini-css-extract-plugin/#minimizing-for-production>
5. How does production site is built using webpack --- <https://webpack.js.org/guides/production/>
6. Setting up perfect devpack server --- <https://linguinecode.com/post/how-to-setup-webpack-dev-server-react-babel>
7. Loaders in details --- <https://webpack.js.org/concepts/loaders/>
8. Understanding babel-preset-env in details --- <https://blog.jakoblind.no/babel-preset-env/>

I hope you found this article useful. Will meet you soon with next one.  

Build composable web applications
=================================

Don't build web monoliths. Use [Bit](https://bit.dev/) to create and compose decoupled software components --- in your favorite frameworks like React or Node. Build scalable and modular applications with a powerful and enjoyable dev experience.

Bring your team to [Bit Cloud](https://bit.cloud) to host and collaborate on components together, and greatly speed up, scale, and standardize development as a team. Start with composable frontends like a Design System or Micro Frontends, or explore the composable backend. [**Give it a try →**](https://bit.dev)  
![](https://miro.medium.com/max/1400/1*ctBUj-lpq4PZpMcEF-qB7w.gif)

Learn More
----------


How We Build Micro Frontends
----------------------------

### Building micro-frontends to speed up and scale our web development process.

blog.bitsrc.io  

How we Build a Component Design System
--------------------------------------

### Building a design system with components to standardize and scale our UI development process.

blog.bitsrc.io  

The Composable Enterprise: A Guide
----------------------------------

### To deliver in 2022, the modern enterprise must become composable.

blog.bitsrc.io  

7 Tools for Faster Frontend Development in 2022
-----------------------------------------------

### Tools you should know to build modern Frontend applications faster, and have more fun.

blog.bitsrc.io  
[](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fvote%2Fbitsrc%2Fb0a5806a92&operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&user=Kannan+Nagasamy&userId=c6778e363b04&source=-----b0a5806a92---------------------clap_footer-----------)  
--
[](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fvote%2Fbitsrc%2Fb0a5806a92&operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&user=Kannan+Nagasamy&userId=c6778e363b04&source=-----b0a5806a92---------------------clap_footer-----------)  
--  
1  
[](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fbookmark%2Fp%2Fb0a5806a92&operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&source=--------------------------bookmark_footer-----------)  

[More from Bits and Pieces](https://blog.bitsrc.io/?source=post_page-----b0a5806a92--------------------------------)
--------------------------------------------------------------------------------------------------------------------

[Follow](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fsubscribe%2Fcollection%2Fbitsrc%2Fb0a5806a92&operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&collection=Bits+and+Pieces&collectionId=5c2fdf847f4a&source=post_page-----b0a5806a92---------------------follow_footer-----------)  
The blog for advanced web and frontend development articles, tutorials, and news. Love JavaScript? Follow to get the best stories.  
[Read more from Bits and Pieces](https://blog.bitsrc.io/?source=post_page-----b0a5806a92--------------------------------)  

Recommended from Medium
-----------------------

[![Websolutionstuff](https://miro.medium.com/fit/c/40/40/1*7ve0d5bZ3-xJdtYDFSLa9w.png)](https://websolutionstuff.medium.com/?source=post_internal_links---------0----------------------------)  
[Websolutionstuff](https://websolutionstuff.medium.com/?source=post_internal_links---------0----------------------------)
[How To Add Summernote Editor In Laravel
---------------------------------------](https://websolutionstuff.medium.com/how-to-add-summernote-editor-in-laravel-cf04e75ef27f?source=post_internal_links---------0----------------------------)
[![How To Add Summernote Editor In Laravel](https://miro.medium.com/focal/112/112/50/50/1*zgX3ZE6732vR2YRiP8SGAQ.png)](https://websolutionstuff.medium.com/how-to-add-summernote-editor-in-laravel-cf04e75ef27f?source=post_internal_links---------0----------------------------)  
[![Websolutionstuff](https://miro.medium.com/fit/c/40/40/1*7ve0d5bZ3-xJdtYDFSLa9w.png)](https://websolutionstuff.medium.com/?source=post_internal_links---------1----------------------------)  
[Websolutionstuff](https://websolutionstuff.medium.com/?source=post_internal_links---------1----------------------------)
[Load More Data in Laravel Using Ajax jQuery
-------------------------------------------](https://websolutionstuff.medium.com/load-more-data-in-laravel-using-ajax-jquery-f954e7027a53?source=post_internal_links---------1----------------------------)
[](https://websolutionstuff.medium.com/load-more-data-in-laravel-using-ajax-jquery-f954e7027a53?source=post_internal_links---------1----------------------------)  
[![Fatiha Zannat](https://miro.medium.com/fit/c/40/40/0*FhhRudqy2IDj4A3w)](https://fatihazannat-s.medium.com/?source=post_internal_links---------2----------------------------)  
[Fatiha Zannat](https://fatihazannat-s.medium.com/?source=post_internal_links---------2----------------------------)
[React.js fundamental
--------------------](https://fatihazannat-s.medium.com/react-js-fundamental-7178020a6075?source=post_internal_links---------2----------------------------)
[](https://fatihazannat-s.medium.com/react-js-fundamental-7178020a6075?source=post_internal_links---------2----------------------------)  
[![Het Patel](https://miro.medium.com/fit/c/40/40/0*-A4I-P2NhEQATKNM)](https://medium.com/@het_45274?source=post_internal_links---------3----------------------------)  
[Het Patel](https://medium.com/@het_45274?source=post_internal_links---------3----------------------------)
[How to make your single-page application Search Engine Optimized using Rendertron
---------------------------------------------------------------------------------](https://medium.com/@het_45274/how-to-make-your-single-page-application-search-engine-optimized-96ce1c24aa97?source=post_internal_links---------3----------------------------)
[![](https://miro.medium.com/focal/112/112/50/50/0*aC86eDvhtx_dNWG8)](https://medium.com/@het_45274/how-to-make-your-single-page-application-search-engine-optimized-96ce1c24aa97?source=post_internal_links---------3----------------------------)  
[![Max Goldstein](https://miro.medium.com/fit/c/40/40/0*3orIh50mT_pjKeSO.JPG)](https://medium.com/@Max_Goldstein?source=post_internal_links---------4----------------------------)  
[Max Goldstein](https://medium.com/@Max_Goldstein?source=post_internal_links---------4----------------------------)  
in  
[HackerNoon.com](https://medium.com/hackernoon?source=post_internal_links---------4----------------------------)
[Elm Semantics for JavaScript Developers
---------------------------------------](https://medium.com/hackernoon/elm-semantics-for-javascript-developers-56a83e5ae23?source=post_internal_links---------4----------------------------)
[](https://medium.com/hackernoon/elm-semantics-for-javascript-developers-56a83e5ae23?source=post_internal_links---------4----------------------------)  
[![Tomas Nilsson](https://miro.medium.com/fit/c/40/40/0*MkPjsC7Bk7Nlf3yZ)](https://tomasnilsson71.medium.com/?source=post_internal_links---------5----------------------------)  
[Tomas Nilsson](https://tomasnilsson71.medium.com/?source=post_internal_links---------5----------------------------)
[Electron + React with Typescript
--------------------------------](https://tomasnilsson71.medium.com/electron-react-with-typescript-7decae392b50?source=post_internal_links---------5----------------------------)
[![](https://miro.medium.com/focal/112/112/50/50/1*aT4mW4L2e-npsMbnQgounA.png)](https://tomasnilsson71.medium.com/electron-react-with-typescript-7decae392b50?source=post_internal_links---------5----------------------------)  
[![Jonathan Brierre](https://miro.medium.com/fit/c/40/40/1*NQlV7JZIFy6PicqAZOpU4A.jpeg)](https://medium.com/@jonathanbrierre?source=post_internal_links---------6----------------------------)  
[Jonathan Brierre](https://medium.com/@jonathanbrierre?source=post_internal_links---------6----------------------------)  
in  
[Better Programming](https://betterprogramming.pub/?source=post_internal_links---------6----------------------------)
[Get to Know the UseState Hook in React.js
-----------------------------------------](https://betterprogramming.pub/get-to-know-the-usestate-hook-in-react-js-d87797cb5a7?source=post_internal_links---------6----------------------------)
[![useState Hook in action](https://miro.medium.com/focal/112/112/50/50/1*VgTrI7fyXouNag3J3bPt8Q.jpeg)](https://betterprogramming.pub/get-to-know-the-usestate-hook-in-react-js-d87797cb5a7?source=post_internal_links---------6----------------------------)  
[![Phil Alive To Learn](https://miro.medium.com/fit/c/40/40/1*ev5j9owaj4gxoLsBUvsh6A.jpeg)](https://x1001000.medium.com/?source=post_internal_links---------7----------------------------)  
[Phil Alive To Learn](https://x1001000.medium.com/?source=post_internal_links---------7----------------------------)  
in  
[十百千實驗室](https://medium.com/十百千實驗室?source=post_internal_links---------7----------------------------)
[Happy LeetCoding
----------------](https://medium.com/十百千實驗室/happy-leetcoding-e82fa03299ff?source=post_internal_links---------7----------------------------)
[![](https://miro.medium.com/focal/112/112/50/50/1*Te_I1XPbAstsehi4Y7FSpg.png)](https://medium.com/十百千實驗室/happy-leetcoding-e82fa03299ff?source=post_internal_links---------7----------------------------)  
[](https://medium.com/?source=post_page-----b0a5806a92--------------------------------)  
[About](https://medium.com/about?autoplay=1&source=post_page-----b0a5806a92--------------------------------)[Help](https://help.medium.com/hc/en-us?source=post_page-----b0a5806a92--------------------------------)[Terms](https://policy.medium.com/medium-terms-of-service-9db0094a1e0f?source=post_page-----b0a5806a92--------------------------------)[Privacy](https://policy.medium.com/medium-privacy-policy-f03bf92035c9?source=post_page-----b0a5806a92--------------------------------)  

Get the Medium app
------------------

[![A button that says 'Download on the App Store', and if clicked it will lead you to the iOS App store](https://miro.medium.com/max/270/1*Crl55Tm6yDNMoucPo1tvDg.png)](https://itunes.apple.com/app/medium-everyones-stories/id828256236?pt=698524&mt=8&ct=post_page&source=post_page-----b0a5806a92--------------------------------)
[![A button that says 'Get it on, Google Play', and if clicked it will lead you to the Google Play store](https://miro.medium.com/max/270/1*W_RAPQ62h0em559zluJLdQ.png)](https://play.google.com/store/apps/details?id=com.medium.reader&source=post_page-----b0a5806a92--------------------------------)  
[Get started](https://medium.com/m/signin?operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&source=post_page--------------------------nav_reg-----------)  
[![Kannan Nagasamy](https://miro.medium.com/fit/c/176/176/0*tZuggF3akejte824)](https://medium.com/@kannankannan18)  
[Kannan Nagasamy
---------------](https://medium.com/@kannankannan18)  
15 Followers  

Someone who always loves to learn and share something new :)  
[Follow](https://medium.com/m/signin?actionUrl=https%3A%2F%2Fmedium.com%2F_%2Fsubscribe%2Fuser%2Fc6778e363b04&operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&user=Kannan+Nagasamy&userId=c6778e363b04&source=post_page-c6778e363b04-------------------------follow_profile-----------)  
[](https://medium.com/m/signin?actionUrl=%2F_%2Fapi%2Fsubscriptions%2Fnewsletters%2F25863abfbb19&operation=register&redirect=https%3A%2F%2Fblog.bitsrc.io%2Fcreate-react-app-without-create-react-app-b0a5806a92&newsletterV3=c6778e363b04&newsletterV3Id=25863abfbb19&user=Kannan+Nagasamy&userId=c6778e363b04&source=--------------------------subscribe_user-----------)  

More from Medium
----------------

[![Manish Mandal](https://miro.medium.com/fit/c/40/40/1*WBGdTZqO937yQmL7PY69Tw.jpeg)](https://manntrix.medium.com/?source=read_next_recirc---------0---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
[Manish Mandal](https://manntrix.medium.com/?source=read_next_recirc---------0---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
in  
[How To React](https://medium.com/how-to-react?source=read_next_recirc---------0---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)
[How to parse or read CSV files in ReactJS
-----------------------------------------](https://medium.com/how-to-react/how-to-parse-or-read-csv-files-in-reactjs-81e8ee4870b0?source=read_next_recirc---------0---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)
[![](https://miro.medium.com/focal/112/112/50/50/1*WsH4vlT47fwiTSBC7F8AdA.jpeg)](https://medium.com/how-to-react/how-to-parse-or-read-csv-files-in-reactjs-81e8ee4870b0?source=read_next_recirc---------0---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
[![Sourabh Bagrecha](https://miro.medium.com/fit/c/40/40/1*MiMv4K8JInA4Gxoxr40TCw.png)](https://medium.com/@sourabhbagrecha?source=read_next_recirc---------1---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
[Sourabh Bagrecha](https://medium.com/@sourabhbagrecha?source=read_next_recirc---------1---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)
[Host/Deploy your React.js Web-App on MongoDB Realm
--------------------------------------------------](https://medium.com/@sourabhbagrecha/host-deploy-your-react-js-web-app-on-mongodb-realm-a64eda9b6993?source=read_next_recirc---------1---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)
[![](https://miro.medium.com/focal/112/112/50/50/1*vv1EJOPNM06pGr9Uvm8IGA.png)](https://medium.com/@sourabhbagrecha/host-deploy-your-react-js-web-app-on-mongodb-realm-a64eda9b6993?source=read_next_recirc---------1---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
[![Mudannayakehiruni](https://miro.medium.com/fit/c/40/40/0*cjBgDKXau4ND3tvU)](https://medium.com/@mudannayakehiruni90?source=read_next_recirc---------2---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
[Mudannayakehiruni](https://medium.com/@mudannayakehiruni90?source=read_next_recirc---------2---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)
[NODEJS and REACT JS
-------------------](https://medium.com/@mudannayakehiruni90/nodejs-and-react-js-47a4cb0db603?source=read_next_recirc---------2---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)
[![](https://miro.medium.com/focal/112/112/50/50/1*2sA6TrLml43eYoUSkjUY0g.png)](https://medium.com/@mudannayakehiruni90/nodejs-and-react-js-47a4cb0db603?source=read_next_recirc---------2---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
[![Neeraj Dana](https://miro.medium.com/fit/c/40/40/1*U1KKYIQu9LNhhfoKC_7bdA.jpeg)](https://neerajdana.medium.com/?source=read_next_recirc---------3---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
[Neeraj Dana](https://neerajdana.medium.com/?source=read_next_recirc---------3---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
in  
[The Javascript](https://javascripttricks.com/?source=read_next_recirc---------3---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)
[React App \| Next js Server side rendering Framework
----------------------------------------------------](https://javascripttricks.com/react-app-next-js-server-side-rendering-framework-bc0ca6d205cd?source=read_next_recirc---------3---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)
[![](https://miro.medium.com/focal/112/112/50/50/0*TaPH2-jKlMuITBJE)](https://javascripttricks.com/react-app-next-js-server-side-rendering-framework-bc0ca6d205cd?source=read_next_recirc---------3---------------------52f3dd6f_646e_46c1_abc9_5faffdafb8ff-------)  
[Help](https://help.medium.com/hc/en-us)  
[Status](https://medium.statuspage.io)  
[Writers](https://about.medium.com/creators/)  
[Blog](https://blog.medium.com)  
[Careers](https://medium.com/jobs-at-medium/work-at-medium-959d1a85284e)  
[Privacy](https://policy.medium.com/medium-privacy-policy-f03bf92035c9)  
[Terms](https://policy.medium.com/medium-terms-of-service-9db0094a1e0f)  
[About](https://medium.com/about?autoplay=1)  
[Knowable](https://knowable.fyi)
