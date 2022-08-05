---
title: Introduction to Node
tags:  blog rtrvl
author: retr0ville
source: https://nodejs.dev/learn/#an-example-nodejs-application
---
Introduction to Node.js  

* Learn
* [Documentation](https://nodejs.org/en/docs/)
* Download
* Community

* *search*
* 
* [GitHub](https://github.com/nodejs/nodejs.dev)
Menu

*offline_bolt*Quick Start
-------------------------

Introduction to Node.js A brief history of Node.js How to install Node.js How much JavaScript do you need to know to use Node.js? Differences between Node.js and the Browser

<!-- -->

*offline_bolt*Getting Started
-----------------------------

The V8 JavaScript Engine Run Node.js scripts from the command line How to exit from a Node.js program How to read environment variables from Node.js How to use the Node.js REPL Node.js, accept arguments from the command line Output to the command line using Node.js Accept input from the command line in Node.js Expose functionality from a Node.js file using exports An introduction to the npm package manager Where does npm install the packages? How to use or execute a package installed using npm The package.json guide The package-lock.json file Find the installed version of an npm package Install an older version of an npm package Update all the Node.js dependencies to their latest version Semantic Versioning using npm Uninstalling npm packages npm global or local packages npm dependencies and devDependencies The npx Node.js Package Runner The Node.js Event Loop Understanding process.nextTick() Understanding setImmediate() Discover JavaScript Timers JavaScript Asynchronous Programming and Callbacks Understanding JavaScript Promises Modern Asynchronous JavaScript with Async and Await The Node.js Event emitter Build an HTTP Server Making HTTP requests with Node.js Get HTTP request body data using Node.js Working with file descriptors in Node.js Node.js file stats Node.js File Paths Reading files with Node.js Writing files with Node.js Working with folders in Node.js The Node.js fs module The Node.js path module The Node.js os module The Node.js events module The Node.js http module Node.js Buffers Node.js Streams Node.js, the difference between development and production Error handling in Node.js How to log an object in Node.js Node.js with TypeScript Asynchronous flow control Node.js with WebAssembly

Introduction to Node.js
=======================

###### TABLE OF CONTENTS

* A Vast Number of Libraries
* An Example Node.js Application
* Node.js Frameworks and Tools

Node.js is an open-source and cross-platform JavaScript runtime environment. It is a popular tool for almost any kind of project!

Node.js runs the V8 JavaScript engine, the core of Google Chrome, outside of the browser. This allows Node.js to be very performant.

A Node.js app runs in a single process, without creating a new thread for every request. Node.js provides a set of asynchronous I/O primitives in its standard library that prevent JavaScript code from blocking and generally, libraries in Node.js are written using non-blocking paradigms, making blocking behavior the exception rather than the norm.

When Node.js performs an I/O operation, like reading from the network, accessing a database or the filesystem, instead of blocking the thread and wasting CPU cycles waiting, Node.js will resume the operations when the response comes back.

This allows Node.js to handle thousands of concurrent connections with a single server without introducing the burden of managing thread concurrency, which could be a significant source of bugs.

Node.js has a unique advantage because millions of frontend developers that write JavaScript for the browser are now able to write the server-side code in addition to the client-side code without the need to learn a completely different language.

In Node.js the new ECMAScript standards can be used without problems, as you don't have to wait for all your users to update their browsers - you are in charge of deciding which ECMAScript version to use by changing the Node.js version, and you can also enable specific experimental features by running Node.js with flags.

A Vast Number of Libraries
--------------------------

npm with its simple structure helped the ecosystem of Node.js proliferate, and now the npm registry hosts over 1,000,000 open source packages you can freely use.

An Example Node.js Application
------------------------------

The most common example Hello World of Node.js is a web server:

This code first includes the Node.js [`http` module](https://nodejs.org/api/http.html).

Node.js has a fantastic [standard library](https://nodejs.org/api/), including first-class support for networking.

The `createServer()` method of `http` creates a new HTTP server and returns it.

The server is set to listen on the specified port and host name. When the server is ready, the callback function is called, in this case informing us that the server is running.

Whenever a new request is received, the [`request` event](https://nodejs.org/api/http.html#http_event_request) is called, providing two objects: a request (an [`http.IncomingMessage`](https://nodejs.org/api/http.html#http_class_http_incomingmessage) object) and a response (an [`http.ServerResponse`](https://nodejs.org/api/http.html#http_class_http_serverresponse) object).

Those 2 objects are essential to handle the HTTP call.

The first provides the request details. In this simple example, this is not used, but you could access the request headers and request data.

The second is used to return data to the caller.

In this case with:

```
         
     
          
      JS
          copy
         
     
         
     
          
      res
          
      .
          
      statusCode
          
       
          
      =
          
       
          
      200
          
      ;
          
      
         
     
         
     
          
      

         
     
```

we set the statusCode property to 200, to indicate a successful response.

We set the Content-Type header:

```
         
     
          
      JS
          copy
         
     
         
     
          
      res
          
      .
          
      setHeader
          
      (
          
      'Content-Type'
          
      ,
          
       
          
      'text/plain'
          
      )
          
      ;
          
      
         
     
         
     
          
      

         
     
```

and we close the response, adding the content as an argument to `end()`:

```
         
     
          
      JS
          copy
         
     
         
     
          
      res
          
      .
          
      end
          
      (
          
      'Hello World\n'
          
      )
          
      ;
          
      
         
     
         
     
          
      

         
     
```

Node.js Frameworks and Tools
----------------------------

Node.js is a low-level platform. In order to make things easy and exciting for developers, thousands of libraries were built upon Node.js by the community.

Many of those established over time as popular options. Here is a non-comprehensive list of the ones worth learning:

* [**AdonisJS**](https://adonisjs.com/): A TypeScript-based fully featured framework highly focused on developer ergonomics, stability, and confidence. Adonis is one of the fastest Node.js web frameworks.
* [**Egg.js**](https://eggjs.org): A framework to build better enterprise frameworks and apps with Node.js \& Koa.
* [**Express**](https://expressjs.com/): It provides one of the most simple yet powerful ways to create a web server. Its minimalist approach, unopinionated, focused on the core features of a server, is key to its success.
* [**Fastify**](https://fastify.io/): A web framework highly focused on providing the best developer experience with the least overhead and a powerful plugin architecture. Fastify is one of the fastest Node.js web frameworks.
* [**FeatherJS**](https://feathersjs.com/): Feathers is a lightweight web-framework for creating real-time applications and REST APIs using JavaScript or TypeScript. Build prototypes in minutes and production-ready apps in days.
* [**Gatsby**](https://www.gatsbyjs.com/): A [React](https://reactjs.org/)-based, [GraphQL](https://graphql.org/) powered, static site generator with a very rich ecosystem of plugins and starters.
* [**hapi**](https://hapi.dev): A rich framework for building applications and services that enables developers to focus on writing reusable application logic instead of spending time building infrastructure.
* [**koa**](http://koajs.com/): It is built by the same team behind Express, aims to be even simpler and smaller, building on top of years of knowledge. The new project born out of the need to create incompatible changes without disrupting the existing community.
* [**Loopback.io**](https://loopback.io/): Makes it easy to build modern applications that require complex integrations.
* [**Meteor**](https://meteor.com): An incredibly powerful full-stack framework, powering you with an isomorphic approach to building apps with JavaScript, sharing code on the client and the server. Once an off-the-shelf tool that provided everything, now integrates with frontend libs [React](https://reactjs.org/), [Vue](https://vuejs.org/), and [Angular](https://angular.io). Can be used to create mobile apps as well.
* [**Micro**](https://github.com/zeit/micro): It provides a very lightweight server to create asynchronous HTTP microservices.
* [**NestJS**](https://nestjs.com/): A TypeScript based progressive Node.js framework for building enterprise-grade efficient, reliable and scalable server-side applications.
* [**Next.js**](https://nextjs.org/): [React](https://reactjs.org) framework that gives you the best developer experience with all the features you need for production: hybrid static \& server rendering, TypeScript support, smart bundling, route pre-fetching, and more.
* [**Nx**](https://nx.dev/): A toolkit for full-stack monorepo development using NestJS, Express, [React](https://reactjs.org/), [Angular](https://angular.io), and more! Nx helps scale your development from one team building one application to many teams collaborating on multiple applications!
* [**Remix**](https://remix.run): Remix is a fullstack web framework for building excellent user experiences for the web. It comes out of the box with everything you need to build modern web applications (both frontend and backend) and deploy them to any JavaScript-based runtime environment (including Node.js).
* [**Sapper**](https://sapper.svelte.dev/): Sapper is a framework for building web applications of all sizes, with a beautiful development experience and flexible filesystem-based routing. Offers SSR and more!
* [**Socket.io**](https://socket.io/): A real-time communication engine to build network applications.
* [**Strapi**](https://strapi.io/): Strapi is a flexible, open-source Headless CMS that gives developers the freedom to choose their favorite tools and frameworks while also allowing editors to easily manage and distribute their content. By making the admin panel and API extensible through a plugin system, Strapi enables the world's largest companies to accelerate content delivery while building beautiful digital experiences.

