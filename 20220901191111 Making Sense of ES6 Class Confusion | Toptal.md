---
title: Making Sense of ES6 Class Confusion | Toptal
tags: android blog rtrvl
author: retr0ville
source: https://www.toptal.com/javascript/es6-class-chaos-keeps-js-developer-up
---
Making Sense of ES6 Class Confusion \| Toptal  
[Developers](https://www.toptal.com/developers)
Hiring? Toptal handpicks [top JavaScript developers](https://www.toptal.com/javascript) to suit your needs.

* Top 3%
* Why
* Clients
* Enterprise
* Community
* Blog
* About Us

<!-- -->

* [Follow us on](https://www.linkedin.com/company/toptal)
* Log In
* Go to Your Profile  
EngineeringAll Blogs  
Icon Chevron  
Icon Close Search  
Filter by  
All Engineering Design Finance Projects Product Toptal Insights  
View all results  
[Engineering](https://www.toptal.com/developers/blog)  
[Design](https://www.toptal.com/designers/blog)  
[Finance](https://www.toptal.com/finance/blog)  
[Projects](https://www.toptal.com/project-managers/blog)  
[Product](https://www.toptal.com/product-managers/blog)  
[Toptal Insights](https://www.toptal.com/insights)  
![Cover image](https://bs-uploads.toptal.io/blackfish-uploads/components/blog_post_page/content/cover_image_file/cover_image/686405/retina_1708x683_cover-es6-class-chaos-keeps-js-developer-up-7eb66a51825cb2fa4d33a57cb7486ed7.png)  
[Back-end](https://www.toptal.com/developers/blog/back-end)  
11 minute read

As a JS Developer, This Is What Keeps Me Up at Night
====================================================

JavaScript is an oddball of a language with numerous approaches to almost any problem. When ES6 added the "class" keyword, did it save the day or just muddy the waters? In this article, Toptal Freelance JavaScript Developer Justen Robertson explores OOP in modern JS.  
Author  
[](https://www.toptal.com/resume/justen-robertson)  
Author  
[Justen Robertson](https://www.toptal.com/resume/justen-robertson)  
Justen has a decade of full-stack JavaScript experience working with the likes of Taylor Swift and the Red Hot Chili Peppers.  
SHARE

* 
* 
*  
SHARE

* 
* 
*  
[JavaScript](https://www.toptal.com/javascript) is an oddball of a language. Though inspired by Smalltalk, it uses a C-like syntax. It combines aspects of procedural, functional, and object-oriented programming (OOP) paradigms. It has [numerous](https://www.toptal.com/javascript/javascript-es6-cheat-sheet), often redundant, approaches to solving almost any conceivable programming problem and is not strongly opinionated about which are preferred. It's weakly and dynamically typed, with a mazelike approach to type coercion that trips up even experienced developers.

JavaScript also has its warts, traps, and questionable features. New programmers struggle with some of its more difficult concepts---think asynchronicity, closures, and hoisting. Programmers with experience in other languages reasonably assume things with similar names and appearances will work the same way in JavaScript and are often wrong. Arrays aren't really arrays; what's the deal with `this`, what's a prototype, and what does `new` actually do?

The Trouble with ES6 Classes
----------------------------

The worst offender by far is new to JavaScript's latest release version, [ECMAScript](https://www.toptal.com/ecmascript) 6 (ES6): *classes*. Some of the talk around classes is frankly alarming and reveals a deep-rooted misunderstanding of how the language actually works:

"JavaScript is finally a *real* object-oriented language now that it has classes!"

Or:

"Classes free us up from thinking about JavaScript's broken inheritance model."

Or even:

"Classes are a safer, easier approach to creating types in JavaScript."

These statements don't bother me because they imply there's something wrong with prototypical inheritance; let's set aside those arguments. These statements bother me because none of them are true, and they demonstrate the consequences of JavaScript's "everything for everyone" approach to language design: It cripples a programmer's understanding of the language more often than it enables. Before I go any further, let's illustrate.

JavaScript Pop Quiz #1: What's the Essential Difference Between These Code Blocks?
----------------------------------------------------------------------------------

    function PrototypicalGreeting(greeting = "Hello", name = "World") {
      this.greeting = greeting
      this.name = name
    }

    PrototypicalGreeting.prototype.greet = function() {
      return `${this.greeting}, ${this.name}!`
    }

    const greetProto = new PrototypicalGreeting("Hey", "folks")
    console.log(greetProto.greet())
    class ClassicalGreeting {
      constructor(greeting = "Hello", name = "World") {
        this.greeting = greeting
        this.name = name
      }

      greet() {
        return `${this.greeting}, ${this.name}!`
      }
    }

    const classyGreeting = new ClassicalGreeting("Hey", "folks")

    console.log(classyGreeting.greet())
The answer here is *there isn't one*. These do effectively the same thing, it's only a question of whether ES6 class syntax was used.

True, the second example is more expressive. For that reason alone, you might argue that `class` is a nice addition to the language. Unfortunately, the problem is a little more subtle.

JavaScript Pop Quiz #2: What Does the Following Code Do?
--------------------------------------------------------

    function Proto() {
      this.name = 'Proto'
      return this;
    }

    Proto.prototype.getName = function() {
      return this.name
    }

    class MyClass extends Proto {
      constructor() {
        super()
        this.name = 'MyClass'
      }
    }

    const instance = new MyClass()

    console.log(instance.getName())

    Proto.prototype.getName = function() { return 'Overridden in Proto' }

    console.log(instance.getName())

    MyClass.prototype.getName = function() { return 'Overridden in MyClass' }

    console.log(instance.getName())

    instance.getName = function() { return 'Overridden in instance' }


    console.log(instance.getName())
The correct answer is that it prints to console:

    > MyClass
    > Overridden in Proto
    > Overridden in MyClass
    > Overridden in instance
If you answered incorrectly, you don't understand what `class` actually is. This isn't your fault. Much like `Array`, `class` is not a language feature, it's *syntactic obscurantism*. It tries to hide the prototypical inheritance model and the clumsy idioms that come with it, and it implies that JavaScript is doing something that it is not.

You might have been told that `class` was introduced to JavaScript to make classical OOP developers coming from languages like Java more comfortable with the ES6 class inheritance model. If you *are* one of those developers, that example probably horrified you. It should. It shows that JavaScript's `class` keyword doesn't come with any of the guarantees that a class is meant to provide. It also demonstrates one of the key differences in the prototype inheritance model: Prototypes are *object instances* , not *types*.

Prototypes vs. Classes
----------------------

The most important difference between class- and prototype-based inheritance is that a class defines a *type* which can be instantiated at runtime, whereas a prototype is itself an object instance.

A child of an ES6 class is another *type* definition which extends the parent with new properties and methods, which in turn can be instantiated at runtime. A child of a prototype is another object *instance* which delegates to the parent any properties that aren't implemented on the child.

*Side note: You might be wondering why I mentioned class methods, but not prototype methods. That's because JavaScript doesn't have a concept of methods. Functions are [first-class](https://en.wikipedia.org/wiki/First-class_function) in JavaScript, and they can have properties or be properties of other objects.*

A class constructor creates an instance of the class. A constructor in JavaScript is just a plain old function that returns an object. The only thing special about a JavaScript constructor is that, when invoked with the `new` keyword, it assigns its prototype as the prototype of the returned object. If that sounds a little confusing to you, you're not alone---it is, and it's a big part of why prototypes are poorly understood.

To put a really fine point on that, a child of a prototype isn't a *copy* of its prototype, nor is it an object with the same *shape* as its prototype. The child has a living reference *to* the prototype, and any prototype property that doesn't exist on the child is a one-way reference to a property of the same name on the prototype.

Consider the following:

    let parent = { foo: 'foo' }
    let child = { }
    Object.setPrototypeOf(child, parent)

    console.log(child.foo) // 'foo'

    child.foo = 'bar'

    console.log(child.foo) // 'bar'

    console.log(parent.foo) // 'foo'

    delete child.foo

    console.log(child.foo) // 'foo'

    parent.foo = 'baz'

    console.log(child.foo) // 'baz'
Note: You'd almost never write code like this in real life---it's terrible practice---but it demonstrates the principle succinctly.

In the previous example, while `child.foo` was `undefined`, it referenced `parent.foo`. As soon as we defined `foo` on `child`, `child.foo` had the value `'bar'`, but `parent.foo` retained its original value. Once we `delete child.foo` it again refers to `parent.foo`, which means that when we change the parent's value, `child.foo` refers to the new value.

Let's look at what just happened (for the purpose of clearer illustration, we're going to pretend these are `Strings` and not string literals, the difference doesn't matter here):

<br />

<br />

The way this works under the hood, and especially the peculiarities of `new` and `this`, are a topic for another day, but Mozilla has [a thorough article about JavaScript's prototype inheritance chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain) if you'd like to read more.

The key takeaway is that prototypes don't define a `type`; they are themselves `instances` and they're mutable at runtime, with all that implies and entails.

Still with me? Let's get back to dissecting JavaScript classes.

JavaScript Pop Quiz #3: How Do You Implement Privacy in Classes?
----------------------------------------------------------------

Our prototype and class properties above aren't so much "encapsulated" as "hanging precariously out the window." We should fix that, but how?

No code examples here. The answer is that you can't.

JavaScript doesn't have any concept of privacy, but it does have closures:

    function SecretiveProto() {
      const secret = "The Class is a lie!"
      this.spillTheBeans = function() {
        console.log(secret)
      }
    }

    const blabbermouth = new SecretiveProto()
    try {
      console.log(blabbermouth.secret)
    }
    catch(e) {
      // TypeError: SecretiveClass.secret is not defined
    }

    blabbermouth.spillTheBeans() // "The Class is a lie!"
Do you understand what just happened? If not, you don't understand closures. That's okay, really---they're not as intimidating as they're made out to be, they're super useful, and you should [take some time to learn about them](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures).

JavaScript Pop Quiz #4: What's the Equivalent to the Above Using the `class` Keyword?
-------------------------------------------------------------------------------------

Sorry, this is another trick question. You can do basically the same thing, but it looks like this:

    class SecretiveClass {
      constructor() {
        const secret = "I am a lie!"
        this.spillTheBeans = function() {
          console.log(secret)
        }
      }

      looseLips() {
        console.log(secret)
      }
    }

    const liar = new SecretiveClass()
    try {
      console.log(liar.secret)
    }
    catch(e) {
      console.log(e) // TypeError: SecretiveClass.secret is not defined
    }
    liar.spillTheBeans() // "I am a lie!"
Let me know if that looks any easier or clearer than in `SecretiveProto`. In my personal view, it's somewhat worse---it breaks idiomatic use of `class` declarations in JavaScript and it doesn't work much like you'd expect coming from, say, Java. This will be made clear by the following:

JavaScript Pop Quiz #5: What Does `SecretiveClass::looseLips()` Do?
-------------------------------------------------------------------

Let's find out:

    try {
      liar.looseLips()
    }
    catch(e) {
      // ReferenceError: secret is not defined
    }
Well... that was awkward.

JavaScript Pop Quiz #6: Which Do Experienced JavaScript Developers Prefer---Prototypes or Classes?
--------------------------------------------------------------------------------------------------

You guessed it, that's another trick question---experienced JavaScript developers tend to avoid both when they can. Here's a nice way to do the above with idiomatic JavaScript:

    function secretFactory() {
      const secret = "Favor composition over inheritance, `new` is considered harmful, and the end is near!"
      const spillTheBeans = () => console.log(secret)

      return {
        spillTheBeans
      }
    }

    const leaker = secretFactory()
    leaker.spillTheBeans()
This isn't just about avoiding the inherent ugliness of inheritance, or enforcing encapsulation. Think about what else you might do with `secretFactory` and `leaker` that you couldn't easily do with a prototype or a class.

For one thing, you can destructure it because you don't have to worry about the context of `this`:

    const { spillTheBeans } = secretFactory()

    spillTheBeans() // Favor composition over inheritance, (...)
That's pretty nice. Besides avoiding `new` and `this` tomfoolery, it allows us to use our objects interchangeably with CommonJS and ES6 modules. It also makes composition a little easier:

    function spyFactory(infiltrationTarget) {
      return {
        exfiltrate: infiltrationTarget.spillTheBeans
      }
    }

    const blackHat = spyFactory(leaker)

    blackHat.exfiltrate() // Favor composition over inheritance, (...)

    console.log(blackHat.infiltrationTarget) // undefined (looks like we got away with it)
Clients of `blackHat` don't have to worry about where `exfiltrate` came from, and `spyFactory` doesn't have to mess around with `Function::bind` context juggling or deeply nested properties. Mind you, we don't have to worry much about `this` in simple synchronous procedural code, but it causes all kinds of problems in asynchronous code that are better off avoided.

With a little thought, `spyFactory` could be developed into a highly sophisticated espionage tool that could handle all kinds of infiltration targets---or in other words, a [façade](https://www.joezimjs.com/javascript/javascript-design-patterns-facade/).

Of course you could do that with a class too, or rather, an assortment of classes, all of which inherit from an `abstract class` or `interface`...except that JavaScript doesn't have any concept of abstracts or interfaces.

Let's return to the greeter example to see how we'd implement it with a factory:

    function greeterFactory(greeting = "Hello", name = "World") {
      return {
        greet: () => `${greeting}, ${name}!`
      }
    }

    console.log(greeterFactory("Hey", "folks").greet()) // Hey, folks!
*You might have noticed these factories are getting more terse as we go along, but don't worry---they do they same thing. The training wheels are coming off, folks!*

That's already less boilerplate than either the prototype or the class version of the same code. Secondly, it achieves encapsulation of its properties more effectively. Also, it has a lower memory and performance footprint in some cases (it may not seem like it at first glance, but the JIT compiler is quietly working behind the scenes to pare down duplication and infer types).

So it's safer, it's often faster, and it's easier to write code like this. Why do we need classes again? Oh, of course, reusability. What happens if we want unhappy and enthusiastic greeter variants? Well, if we're using the `ClassicalGreeting` class, we probably jump directly into dreaming up a class hierarchy. We know we'll need to parameterize the punctuation, so we'll do a little refactoring and add some children:

    // Greeting class
    class ClassicalGreeting {
      constructor(greeting = "Hello", name = "World", punctuation = "!") {
        this.greeting = greeting
        this.name = name
        this.punctuation = punctuation
      }

      greet() {
        return `${this.greeting}, ${this.name}${this.punctuation}`
      }
    }

    // An unhappy greeting
    class UnhappyGreeting extends ClassicalGreeting {
      constructor(greeting, name) {
        super(greeting, name, " :(")
      }
    }

    const classyUnhappyGreeting = new UnhappyGreeting("Hello", "everyone")

    console.log(classyUnhappyGreeting.greet()) // Hello, everyone :(

    // An enthusiastic greeting
    class EnthusiasticGreeting extends ClassicalGreeting {
      constructor(greeting, name) {
    	super(greeting, name, "!!")
      }

      greet() {
    	return super.greet().toUpperCase()
      }
    }

    const greetingWithEnthusiasm = new EnthusiasticGreeting()

    console.log(greetingWithEnthusiasm.greet()) // HELLO, WORLD!!
It's a fine approach, until someone comes along and asks for a feature that doesn't fit cleanly into the hierarchy and the whole thing stops making any sense. Put a pin in that thought while we try to write the same functionality with factories:

    const greeterFactory = (greeting = "Hello", name = "World", punctuation = "!") => ({
      greet: () => `${greeting}, ${name}${punctuation}`
    })

    // Makes a greeter unhappy
    const unhappy = (greeter) => (greeting, name) => greeter(greeting, name, ":(")

    console.log(unhappy(greeterFactory)("Hello", "everyone").greet()) // Hello, everyone :(

    // Makes a greeter enthusiastic
    const enthusiastic = (greeter) => (greeting, name) => ({
      greet: () => greeter(greeting, name, "!!").greet().toUpperCase()
    })

    console.log(enthusiastic(greeterFactory)().greet()) // HELLO, WORLD!!
It's not obvious that this code is better, even though it's a bit shorter. In fact, you could argue that it's harder to read, and maybe this is an obtuse approach. Couldn't we just have an `unhappyGreeterFactory` and an `enthusiasticGreeterFactory`?

Then your client comes along and says, "I need a new greeter that is unhappy and wants the whole room to know about it!"

    console.log(enthusiastic(unhappy(greeterFactory))().greet()) // HELLO, WORLD :(

If we needed to use this enthusiastically unhappy greeter more than once, we could make it easier on ourselves:

    const aggressiveGreeterFactory = enthusiastic(unhappy(greeterFactory))

    console.log(aggressiveGreeterFactory("You're late", "Jim").greet())
There are approaches to this style of composition that work with prototypes or classes. For example, you could rethink `UnhappyGreeting` and `EnthusiasticGreeting` as [decorators](https://en.wikipedia.org/wiki/Decorator_pattern). It would still take more boilerplate than the functional-style approach used above, but that's the price you pay for the safety and encapsulation of *real* classes.

The thing is, in JavaScript, you're not getting that automatic safety. JavaScript frameworks that emphasize `class` usage do a lot of "magic" to paper over these kinds of problems and force classes to behave themselves. Have a look at Polymer's `ElementMixin` [source code](https://github.com/Polymer/polymer/blob/master/lib/mixins/element-mixin.js) some time, I dare you. It's arch-wizard levels of JavaScript arcana, and I mean that without irony or sarcasm.

Of course, we can fix some of the issues discussed above with `Object.freeze` or `Object.defineProperties` to greater or lesser effect. But why imitate the form without the function, while ignoring the tools JavaScript *does* natively provide us that we might not find in languages like Java? Would you use a hammer labeled "screwdriver" to drive a screw, when your toolbox had as actual screwdriver sitting right next to it?

Finding the Good Parts
----------------------

JavaScript developers often emphasize the language's good parts, both colloquially and in reference to [the book of the same name](https://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742). We try to avoid the traps set by its more questionable language design choices and stick to the parts that let us write clean, readable, error-minimizing, reusable code.

There are reasonable arguments about which parts of JavaScript qualify, but I hope I've convinced you that `class` is not one of them. Failing that, hopefully you understand that inheritance in JavaScript can be a confusing mess and that `class` neither fixes it nor spares you having to understanding prototypes. Extra credit if you picked up on the hints that object-oriented design patterns work fine without classes or ES6 inheritance.

I'm not telling you to avoid `class` entirely. Sometimes you need inheritance, and `class` provides cleaner syntax for doing that. In particular, `class X extends Y` is much nicer than the old prototype approach. Beside that, many popular front-end frameworks encourage its use and you should probably avoid writing weird non-standard code on principle alone. I just don't like where this is going.

In my nightmares, a whole generation of JavaScript libraries are written using `class`, with the expectation that it will behave similarly to other popular languages. Whole new classes of bugs (pun intended) are discovered. Old ones are resurrected that could easily have been left in the Graveyard of Malformed JavaScript if we hadn't carelessly fallen into the `class` trap. Experienced JavaScript developers are plagued by these monsters, because what is popular is not always what is good.

Eventually we all give up in frustration and start reinventing wheels in Rust, Go, Haskell, or who knows what else, and then compiling to Wasm for the web, and new web frameworks and libraries proliferate into multilingual infinity.

It really does keep me up at night.  

Understanding the basics
------------------------

### What is ECMAScript 6?

ES6 is the latest stable implementation of ECMAScript, the open standard on which JavaScript is based. It adds a number of new features to the language including an official module system, block-scoped variables and constants, arrow functions, and numerous other new keywords, syntaxes, and built-in objects.

### Is ES6 the latest ECMAScript version?

ES6 (ES2015) is the most recent standard that is stable and fully implemented (except for proper tail calls and some nuances) in the latest versions of major browsers and other JS environments. ES7 (ES2016) and ES8 (ES2017) are also stable specs, but implementation is quite mixed.

### Is ES6 object-oriented?

JavaScript has strong support for object-oriented programming, but it uses a different inheritance model (prototypical) compared to most popular OO languages (which use classical inheritance). It also supports procedural and functional programming styles.

### What are ES6 classes?

In ES6, the "class" keyword and associated features are a new approach to creating prototype constructors. They are not true classes in a way that would be familiar to users of most other object-oriented languages.

### Which keywords can be used to implement inheritance in ES6?

One can implement inheritance in JavaScript ES6 through the "class" and "extends" keywords. Another approach is via the "constructor" function idiom plus the assignment of functions and static properties to the constructor's prototype.

### What is prototype inheritance in JavaScript?

In prototypical inheritance, prototypes are object instances to which child instances delegate undefined properties. In contrast, classes in classical inheritance are type definitions, from which child classes inherit methods and properties during instantiation.  
Tags
[JavaScript](https://www.toptal.com/developers/blog/tags/javascript) [OOP](https://www.toptal.com/developers/blog/tags/oop)  
Freelancer? Find your next job.  
[JavaScript Developer Jobs](https://www.toptal.com/freelance-jobs/developers/javascript)  
[View full profile](https://www.toptal.com/resume/justen-robertson)  
Justen Robertson

Freelance JavaScript Developer  
About the author

Justen is a full-stack JavaScript developer with over a decade of experience. He has worked on projects for some of the biggest brands in the publishing and recording industries and has worked directly with small businesses and nonprofits in many fields. His broad skillset enables him to cover all the web technology needs of small businesses and startups or to fill the gaps in larger teams.  
[Hire Justen](https://www.toptal.com/hire?interested_in=developers&skill=javascript)  

Comments
--------

Julian G.  
Hi! I'm not a JS developer, not even close a "bad" JS developer, however I use it from time to time as I'm a Qt / QML developer. Regarding the statement: \`\`\` const instance = new MyClass() console.log(instance.getName()) Proto.prototype.getName = function() { return 'Overridden in Proto' } console.log(instance.getName()) MyClass.prototype.getName = function() { return 'Overridden in MyClass' } console.log(instance.getName()) \`\`\` I do not feel horrified, in fact I found this very alike to C pointers to functions (which is the polymorphic mechanism C has), I have to say that I like the mech. I dislike the .prototype. syntax (it seems to me quite complex). Good article, thanks.  
Justen Robertson  
Sure, and that's a much closer analogy to what's happening in Javascript too. I agree that the whole .prototype. syntax is clumsy. Likewise, thanks for your thoughts :)  
Arsenii Fomin  
Thank you for the great article! Spent 10 minutes to understand how "enthusiastic(unhappy(greeterFactory))().greet()" works :) As for my experience, I came to web development from solid (or better say S.O.L.I.D.) C++ background 3 years ago with a lot of incapsulation in my head. I have heard a lot of bad things about javascript and decided to find a good book to understand what to avoid, read "Good parts of javascript", started to use javascript in the projectes and become a fan of the language. When you understand that to solve any problem you basically need only one tool - function (which is the same time function pointer/object/closure/"struct with functions"), it's really impressive in comparison with C++, where you need to combine classes, inheritance, templates, pointers every time to solve a simple problem. And in the most cases you never need classess, new, this and all that stuff in javascript. Btw why haven't you mentioned possibility to have private fields when creating new obects via composition?  
Justen Robertson  
Thanks :) JavaScript is much less of a monster when you stick to a narrow subset of its features that compliment eachother. Yeah I would have liked to get into more depth about how to achieve the equivalent of private fields. There are some great approaches involving closures with Object.defineProperties to control object descriptors that I frequently employ, but I didn't want to meander too deep into the weeds on that. Maybe in a future article.  
papoola  
Thanks for the great article! Had also trouble understanding \`enthusiastic(unhappy(greeterFactory))().greet()\`  
schollii  
Very interesting article. For me the prototype and class examples were easy and no surprises (perhaps having programmed for 30 years in many languages helps). I also found the closures easy, but not so the composition of greeters, and based on comments by others, I'm not the only one. So I'm not tempted to use that kind of composition although I really like your example of how closures can increase encapsulation by not exposing attributes that ought to be private but in js couldn't if it weren't for that technique. The greeter example to me should never be used in practice but there is serious food for thought there, no doubt, so I'll certainly keep an eye open for variations on the same theme. Thanks for an interesting read!  
Justen Robertson  
Thanks :) It's true, in real life you probably would not do something so complicated to solve such a simple problem. Of course you also probably wouldn't create a class hierarchy to solve the problem! There are times when this kind of approach is useful though, in cases where something more straightforward isn't possible.  
monserAR  
really very interesting and informative article, by reading this we can add to our insight \<a href="https://monsterar.net/"\>perusahaan virtual reality indonesia\</a\>  
Nihar Shah  
This article is very much in deep. So it is useful for those who wants to develop their site in java. Our \<a href="http://www.webmynesystems.com/hire-node-js-developer.php"\>dedicated nodejs developers on hiring\</a\> works on java at affordable cost.  
Michael Stelly  
I agree. There is definitely a lot of room for improvement with JS. However, I do not agree with your \<i\>scary-monster-under-the-bed\</i\> mischaracterization of it. I've built mobile apps with JS for over 10 years, most recently in the React Native framework. It's been both challenging and rewarding. I learn something new every day. Let me ask you this (because I really don't understand the crux of the post): - Do other languages handle strongly-typed data better? Yep. - Do they coerce more consistent design and/or development through a more consistent set of tools? Sure do. - Conversely, do they provide a broader scope of utility or application than JS? You tell me. I sat no. - Do they have a higher developer adoption rate than JS? No. - Do more businesses around the world bet their company on it than JS? No. - Are all the developers who bet their careers on it and companies who bet their businesses on it simply that stupid and would be better served chucking the whole mess for one of your chosen ones? - Why, then, all the salty hate? That's how it reads to me, at any rate. The undercurrent of disparagement has me wondering, "If you dislike it that much, why not pick any one of dozens of alternatives." I realize this article is dated. Your opinion may have softened. But as I scrolled through the comments, I found no one willing to disagree with your opinion. I thought it incumbent on me to at least provide a differing view.  
Mirko  
Very nice article! I just have one question left over, maybe because I don't know about the internals of JavaScript: If I use these factories, will they not create new methods for the produced objects every time I call them? Wouldn't that be more inefficient than having a method defined once in the prototype? Or would you define the method once somewhere outside the factory and then reference it?  
Matthijs Wensveen  
I feel that you have mistaken valid criticism for salty hate. The criticism is about the new(ish) class feature in ES6 (and to a lesser extent the underlying prototype based features that are semi-hiden by this), and not about the language itself. I consider it a good thing that experts in the field highlight the parts of their expertise that they consider bad, rather than evangelizing blindly. Books like "JavaScript: The Good Parts" and "Better, Faster, Lighter Java" are great examples of critical but highly useful books about their respective subject of expertise.  
Adelchi Pelizzo  
Seems to me the more I seek clarification, the more I get confused. Would the first example be still valid this way: \<code\> function PrototypicalGreeting(greeting = "Hello", name = "World") { this.greeting = greeting this.name = name greet = function() { return \`${this.greeting}, ${this.name}! } } \</code\>  
David Mauas  
Interesting. Nevertheless - there essentially is no difference in C++ \& C between class and struct... struct is just a { } a data structure... Classes specifically, and OOP in general, IMO, are great because they facilitate THINKING about things as IF they were objects.. They help us \*humans\* see things more clearly. Organize. Sure - we could write \*everything\* in assembly, too. There is no difference. Higher-level languages basically abstract things into a different semantic - that is ALL their purpose. So - yes - classes in JS are not "really" classes. But if they help a human organize things - even a bit - in this messy, messy language - they are wonderful. And in general - even without the inheritance, interfaces, etc - classes are \*truly\* magnificent! No large-scale application (truly, really large) - could exist without OOP. (and strong types, too) It is time-tested. Just as strong-types prevent problems - despite not really being any different - it's all semantics! So despite "class" being "function" in disguise - I would choose it because it does have advantages. Just as being polite, and speaking nicely to others. Just as a million semantic things which make our lives so much better... please, thank you, have a nice day :) Semantics make a \*world\* of a difference. That is my point of view.  
Cihan Deniz  
AFAIK below factory creates a new function for every time it is called. \<code\> function greeterFactory(greeting = "Hello", name = "World") { return { greet: () =\> \`${greeting}, ${name}!\` } } \</code\> I remember making this mistake and creating the slowest component. And then I switched to prototypes, so number of function instances decreased to one per prototype. Let me give a quick example; \<code\> const a = { greet: () =\> 'hello world' }; const b = { greet: () =\> 'hello world' }; \</code\> Above code has two functions declared, but below has only one. \<code\> function greet() { return 'hello world'; } const a = { greet: greet }; const b = { greet: greet }; \</code\> But that was like 15 years ago, so I'm not sure if my point is still valid or not, I'm just asking if it is...  
ytkimirti  
Amazing article. This resolved a lot of issues I had with prototypes even tho your goals was to confuse us :D I learned too much from this article thank you soo much :)  
Charles Robertson  
\<code\>If you are one of those developers, that example probably horrified you\</code\> This is assuming you think that a JS Class should follow the way classes in other languages work? Why is it not possible for JavaScript to follow its own set of rules, which it does? Every language has its own idiosyncrasies. As long as one is clear about the rules of a language, everything is fine. Personally, I find the \<b\>class\</b\> keyword in JavaScript makes code look cleaner. I think most people understand that is it is just syntactic sugar, like the \<b\>async/await\</b\> keyword.  
hhvdblom  
I am a C/C#/C++ developer AND a very experienced Javascript developer. I welcomed the class in Javascript very much. The class encapsulation fits my projects very well.  
hhvdblom  
C is developed in 1972. Its still alive and kicking. Javascript was crap but getting better. Its going the C direction and thats good. Negatives invent "syntactic sugar" but classes are just better a d the full way to go. Why the negatives against classes? Because a lot of code needs to be ported to it. I read a lot of old javascript code and that sucks a lot.  
hhvdblom  
Yes you are right and to the point! Prototypes need to be hidden, internal and not directly used.  
hhvdblom  
Yes you are right. This article goes back to the old Javascript style but classes are the way to go if he likes it or not.  
Justen Robertson  
Sorry for the very belated reply! I think you've misread me here - and no surprise, given the amount of hate that certain languages get online. It would be easy to take this as yet another "10 reasons I hate javascript" article. But this is about one particular language feature - classes. And some criticism of prototypes. Not the language as a whole. On the contrary, my opinion hasn't changed on it at all. If anything it has hardened, and I lean more on functional-style code and factories today than I did when I wrote this. Unfortunately my "fear" here is already crawling out from under the bed. I see more libraries and modules built in WASM every day, often explicitly in order to avoid javascript and its quirks. Maybe a polyglot web is not the worst thing in the world, but it's a significant divergence from the dream of a transparent and open web.  
Justen Robertson  
That's sort of the problem I have with classes - unfortunately they don't do encapsulation any different than javascript already did with prototypes. And prototypes were already a pretty inferior way of achieving encapsulation. Prototypes give us \<i\>inheritance\</i\>, which is arguably the least useful concept in the OOP paradigm - a rant for another day! So class didn't actually give us anything new, other than the false impression that javascript had classes. What it did give us us was a cleaner way to write prototypes - something that already existed - albeit with a confusing keyword.  
Justen Robertson  
In general, yes - I think well-understood keywords should go out of their way to behave as they are commonly understood to behave in other languages. At a minimum, they certainly shouldn't \<i\>disguise\</i\> a feature as another unrelated feature in order to make the language feel more familiar. Async/await is actually a perfect counter-example. It behaves analogously to its peers in other languages, while being sugar for something that already existed and worked well in javascript (promises). In fact you can use promises and async/await completely interchangeably, which is very useful. I am a big fan of that approach.  
Justen Robertson  
Yes, you're absolutely right. That example will create a new instance of the function each time it is called. I omitted this fact for brevity (the article was already too long!) In general when you are dealing with very large numbers of objects, or many objects being created and destroyed in quick succession, you will have performance problems. Prototypes can help here and sometimes they're the right answer, but often what you're dealing with is related to garbage collection, in which case prototypes will only reduce the problem by some fraction, not eliminate it. The best answer is often to avoid doing this in the first place. Find a way to not have to create and destroy tons of objects. If you can't do that, object pools are often your silver bullet.  
Justen Robertson  
\<blockquote\>Classes specifically, and OOP in general, IMO, are great because they facilitate THINKING about things as IF they were objects..\</blockquote\> I am not so convinced this is true. Modularity and encapsulation are important, but thinking of your code as if it was a physical object (say a machine or a tool) is often a false analogy. I escaped the "OOP Cult" a long time ago and found there many different ways to think of code that are often much more useful. This is a rant for another day, and one already made better by other people, but in reply to your whole premise: the notion that large-scale applications cannot exist without OOP is an article of faith unsupported by facts. For example most of our internet infrastructure today runs atop the linux kernel, which is very large, very important, has innumerable contributors and a nearly 30 year history of development, and has never been and could not be object-oriented. Although it does embrace modularity and encapsulation, concerns which are orthogonal to inheritance, message-oriented interfaces and other things that come with the OOP package. Similarly OOP is almost completely unused in scientific simulation, data analysis, commercial video games, and in many other fields that OOP evangelism conveniently ignores. These all certainly qualify as "truly, really large" scale. A typical high-end video game will employ hundreds of people, take half a decade to complete, have millions of customers, and require on-going support and online services for another half-decade after release. And yet you don't see OOP being applied very often in game programming because it's a bad fit (the Unity game engine is a notable exception). You'd think it was the perfect fit of course, if you came up in the OOP school (isn't a video game chock full of virtual objects, and don't they have many hierarchical relationships?) but it turns out that the way a game engine must manipulate its data in order to achieve acceptable performance is incompatible with that paradigm. I'll end up writing another article here if I keep going, so instead I recommend searching for good criticisms of OOP and what other paradigms have to offer.  
Justen Robertson  
See my reply to the OP for why I disagree :)  
Justen Robertson  
Yes, you're correct. Most of the time this is not a problem, but as in your StackOverflow post it can become one when you're creating tons of objects. To add to the answers there the performance hitches with large numbers of objects usually come from instantiating or garbage collecting those objects. Object pools are a great way to solve this problem, and worth looking into if you need to deal with large piles of homogeneous objects.  
David Moore  
I figured out a very annoying thing here: I found that in node, there's the following situation: \<code\>console.log(Object.getPrototypeOf(greetProto)) //PrototypicalGreeting { greet: \[Function\] } console.log(Object.getPrototypeOf(classyGreeting)) //ClassicalGreeting {}\</code\> This is solved in this stackoverflow question: \<a href="https://stackoverflow.com/a/44186329/17616747"\>https://stackoverflow.com/a/44186329/17616747\</a\> , where it's stated "Methods/properties created through the class syntax are non-enumerable and it seems that the environment you log the value in doesn't show non-enumerable properties. console.log is not standardized, so different outputs in different environments have to be expected." So there's a difference in whether the prototype properties are enumerable. Yeesh. Hopefully this helps someone else out!  
Justen Robertson  
Ah, yes that's a good catch. You can make properties of a class instance enumerable through the \<code\>Object.defineProperty\</code\> method if you'd like them to be. One key thing to remember is that non-enumerable properties are still exposed on the object; they just won't appear in enumerations like \<code\>for ... in\</code\>. So making a property enumerable or non-enumerable does not relate to concepts like privacy or encapsulation. This is another of those weird gotchas that makes me think the whole notion of introducing class into JS was a mistake. JS just fundamentally does not work like Java and other classical OOP languages, despite superficial similarities. The list of edge cases and broken expectations class introduced is innumerable, pun intended.
Please enable JavaScript to view the [comments powered by Disqus.](https://disqus.com/?ref_noscript) [comments powered by Disqus](https://disqus.com)  
World-class articles, delivered weekly.  
Get great content

Subscription implies consent to our privacy policy  

Thank you!  
Check out your inbox to confirm your invite.  

Trending Articles
-----------------

[Engineering](https://www.toptal.com/developers/blog) Icon Chevron [Web Front-end](https://www.toptal.com/developers/blog/web-front-end)  

### [The 10 Most Common JavaScript Issues Developers Face](https://www.toptal.com/javascript/10-most-common-javascript-mistakes)

[Engineering](https://www.toptal.com/developers/blog) Icon Chevron [Mobile](https://www.toptal.com/developers/blog/mobile)  

### [Future-proof Your Android Code, Part 1: Functional and Reactive Programming Foundations](https://www.toptal.com/android/functional-reactive-programming-part-1)

[Engineering](https://www.toptal.com/developers/blog) Icon Chevron [Web Front-end](https://www.toptal.com/developers/blog/web-front-end)  

### [A .NET Programmer's Guide to CancellationToken](https://www.toptal.com/asp-dot-net/dotnet-programmer-guide-to-cancellationtoken)

[Engineering](https://www.toptal.com/developers/blog) Icon Chevron [Web Front-end](https://www.toptal.com/developers/blog/web-front-end)  

### [.NET on Linux: Simpler Than It Seems](https://www.toptal.com/asp-dot-net/dotnet-on-linux-simpler-than-it-seems)

See our related talent
[JavaScript](https://www.toptal.com/javascript) [ECMAScript 6](https://www.toptal.com/ecmascript) [Back-end](https://www.toptal.com/back-end) [Front-end](https://www.toptal.com/front-end)  
Freelancer? Find your next job.  
[JavaScript Developer Jobs](https://www.toptal.com/freelance-jobs/developers/javascript)  
Hire the author  
[View full profile](https://www.toptal.com/resume/justen-robertson)  
Justen Robertson

Freelance JavaScript Developer  

Read Next
---------

[](https://www.toptal.com/android/functional-reactive-programming-part-1)  
[Engineering](https://www.toptal.com/developers/blog) Icon Chevron [Mobile](https://www.toptal.com/developers/blog/mobile)  

### [Future-proof Your Android Code, Part 1: Functional and Reactive Programming Foundations](https://www.toptal.com/android/functional-reactive-programming-part-1)

World-class articles, delivered weekly.  
Sign Me Up

Subscription implies consent to our privacy policy  

Thank you!  
Check out your inbox to confirm your invite.  
World-class articles, delivered weekly.  
Sign Me Up

Subscription implies consent to our privacy policy  

Thank you!  
Check out your inbox to confirm your invite.  

Toptal Developers
-----------------

* [Algorithm Developers](https://www.toptal.com/algorithms)
* [Angular Developers](https://www.toptal.com/angular)
* [AWS Developers](https://www.toptal.com/aws)
* [Azure Developers](https://www.toptal.com/azure)
* [Big Data Architects](https://www.toptal.com/big-data)
* [Blockchain Developers](https://www.toptal.com/blockchain)
* [Business Intelligence Developers](https://www.toptal.com/business-intelligence)
* [C Developers](https://www.toptal.com/c)
* [Computer Vision Developers](https://www.toptal.com/computer-vision)
* [Django Developers](https://www.toptal.com/django)
* [Docker Developers](https://www.toptal.com/docker)
* [Elixir Developers](https://www.toptal.com/elixir)
* [Go Engineers](https://www.toptal.com/go)
* [GraphQL Developers](https://www.toptal.com/graphql)
* [Jenkins Developers](https://www.toptal.com/jenkins)
* [Kotlin Developers](https://www.toptal.com/kotlin)
* [Kubernetes Experts](https://www.toptal.com/kubernetes)
* [Machine Learning Engineers](https://www.toptal.com/machine-learning)
* [Magento Developers](https://www.toptal.com/magento)
* [.NET Developers](https://www.toptal.com/dot-net)
* [R Developers](https://www.toptal.com/r)
* [React Native Developers](https://www.toptal.com/react-native)
* [Ruby on Rails Developers](https://www.toptal.com/ruby-on-rails)
* [Salesforce Developers](https://www.toptal.com/salesforce)
* [SQL Developers](https://www.toptal.com/sql)
* [Sys Admins](https://www.toptal.com/sys-admin)
* [Tableau Developers](https://www.toptal.com/tableau)
* [Unreal Engine Developers](https://www.toptal.com/unreal-engine)
* [Xamarin Developers](https://www.toptal.com/xamarin)
* View More Freelance Developers  
Join the Toptal^®^ community.  
Hire a Developer OR Apply as a Developer  

### Most In-demand Talent

* iOS Developers
* Front-end Developers
* UX Designers
* UI Designers
* Financial Modeling Consultants
* Interim CFOs
* Digital Project Managers
* AWS Experts  

### About

* Top 3%
* Clients
* Freelance Developers
* Freelance Designers
* Freelance Finance Experts
* Freelance Project Managers
* Freelance Product Managers
* Freelance Jobs
* Specialized Services
* Utilities \& Tools
* Research \& Analysis Center
* About Us  

### Contact

* Contact Us
* Press Center
* Careers
* FAQ  

### Social

* [](https://www.linkedin.com/company/toptal "LinkedIn")
* [](https://twitter.com/toptal "Twitter")
* [](https://www.facebook.com/toptal "Facebook")
* [](https://www.instagram.com/toptal/ "Instagram")  
The World's Top Talent, On Demand®  
Copyright 2010 - 2022 Toptal, LLC

* Privacy Policy
* Website Terms
* Accessibility  
By continuing to use this site you agree to our [Cookie Policy](https://www.toptal.com/cookie-policy).  
Got it  
![](https://www.facebook.com/tr?id=463369723801939&ev=ViewContent&noscript=1)
