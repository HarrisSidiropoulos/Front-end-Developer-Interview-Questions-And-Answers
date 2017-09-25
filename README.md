# Front-end Job Interview Questions and Answers

This file contains a number of front-end interview questions from [the original
repository](https://github.com/h5bp/Front-end-Developer-Interview-Questions)
and answers [I](https://github.com/noraesae) answered.

## About contribution

This repository is not to make the answers complete with people. This is to fill my personal answers to the original questions. Therefore, I am afraid I do not merge others' answers, and any PR concerning it will be silently closed.

The questions and some of its contents are from
[the original repository](https://github.com/h5bp/Front-end-Developer-Interview-Questions).
If interested in getting involved, it would be the right place.

## Table of Contents

  1. **[General Questions](#general-questions)** - *[Answers](answers/general-questions.md)*
  1. **[HTML Questions](#html-questions)** - *[Answers](answers/html-questions.md)*
  1. **[CSS Questions](#css-questions)** - *[Answers](answers/css-questions.md)*
  1. **[JS Questions](#js-questions)** - *[Answers](answers/js-questions.md)*
  1. **[Testing Questions](#testing-questions)** - *[Answers](answers/testing-questions.md)*
  1. **[Performance Questions](#performance-questions)** - *[Answers](answers/performance-questions.md)*
  1. **[Network Questions](#network-questions)** - *[Answers](answers/network-questions.md)*
  1. **[Coding Questions](#coding-questions)** - *[Answers](answers/coding-questions.md)*
  1. **[Fun Questions](#fun-questions)** - *[Answers](answers/fun-questions.md)*

  # General Questions

  #### What did you learn yesterday/this week?

  I studied about a Node.js ORM called Bookshelf.js and Express middleware
  implementation. I also solved some problems in
  [Project Euler](https://projecteuler.net) using Haskell, in which I am
  currently interested

  #### What excites or interests you about coding?

  I'm generally interested in quite everything about coding. Nowadays I'm
  especially fascinated by Haskell, one of the most beautiful languages I've
  ever experienced.

  Also I like to create tools and services I and many others can be helped by
  and enjoy using.

  #### What is a recent technical challenge you experienced and how did you solve it?

  Recently I worked on building a web service and we needed to write test cases
  for APIs of it. When writing a test case, it needs several database entities
  which will be used in the test case, and it is really a pain to write all the
  insertion code for the database and cleanup at the end.

  To resolve the problem, I implemented concepts called 'state' and 'environment'.
  'State' refers to a database instance which a session contains. 'Environment'
  helps the 'state' manage its own entities. With the concepts, entities can be
  created and managed easily in each test session and also cleaned all together
  with the `cleanup` method implemented in a state instance.

  #### What UI, Security, Performance, SEO, Maintainability or Technology considerations do you make while building a web application or site?

  - **UI**: I like minimal UI which contains only what it should. I believe it
    results in the better user experience, as a user knows what to do
    intuitively.
  - **Security**: I always try to make both frontend and backend secure,
    concerning CSRF, XSS, etc.
  - **Performance**: I consider space and time complexity for the algorithms and
    logics I use and write.
  - **SEO**: Set meta tags for search engines and consider and consider
    server-side rendering for SPA.
  - **Maintainability**: Try to keep the source code consistent and make objects
    immutable. Use statically typed languages such as TypeScript. Use CI with
    tests and lints.
  - **Technology**: I like to learn new technologies, but if the project is
    in production, I would consider using technologies which is well-documented
    and widely used.

  #### Talk about your preferred development environment.

  I like to work in terminal shell environments. For the time being, my favourite
  dev environment are like below:

  - OS X
  - iTerm2
  - Tmux
  - Vim

  Nevertheless, I don't want to say they are the silver bullets for everything. I
  always try to find the best environment for each language and requirement.

  #### Which version control systems are you familiar with?

  Git. Not really familiar with others, but at least have experience of
  Subversion and Mercurial too.

  #### Can you describe your workflow when you create a web page?

  I usually use Node.js to build a web page, so will describe the workflow with
  it.

  1. Decide a CSS preprocessor. I may consider using SCSS, but Less and Stylus
     are also viable options.
  1. Decide a HTML template engine. I may go with Pug(formerly Jade).
  1. Decide a JavaScript preprocessor or other languages being compiled to it.
     I may go with TypeScript or ES6 with Babel.
  1. Decide a task manager. I recently like to just use NPM scripts instead of
     using huge task managers like Gulp or Grunt.
  1. Write tests and make them fail.
  1. Write app code and check the tests succeed.
  1. Set CI.
  1. Publish the code and check a task in CI succeed.

  #### If you have 5 different stylesheets, how would you best integrate them into the site?

  Use a CSS preprocessor to nest them with `@import` statements in class names
  for each stylesheet, and merge them into a built file. In production, minify
  the built file with a CSS minifier.

  #### Can you describe the difference between progressive enhancement and graceful degradation?

  **Progressive enhancement** is a way to implement a web page where basic
  features, which are supported by most environments, are implemented first and
  then progressively enhance them for advanced environments.

  On the other hand, **graceful degradation** is an opposite. The advanced
  features are freely implemented at any time, and additional works are done
  to support the environment where the features don't work well.

  #### How would you optimize a website's assets/resources?

  Minimise CSS and JavaScript using minifier(or uglifier), archive them using
  gzip, use separated file servers, use CDN, etc.

  #### How many resources will a browser download from a given domain at a time?

  It depends on browser implementations. Usually 6 to 8 in the modern browsers,
  and less in the old browsers.

  ###### What are the exceptions?

  When we use several subdomains pointing the same domain, we can increase the
  concurrency level of the download.

  #### Name 3 ways to decrease page load (perceived or actual load time).

  - Use minifier and gzip to decrease the page size *- actual*
  - Show spinner or progress bar *- perceived*
  - Preload the page before actually loading it using libraries like
    [InstantClick](http://instantclick.io) *- both actual and perceived*

  #### If you jumped on a project and they used tabs and you used spaces, what would you do?

  - I would use tabs because it is the convention used for the project.
  - Introduce a linter or other scripts to ensure indentations are consistent
  - Use a tool like [EditorConfig](http://editorconfig.org) to configure editors
    team members are using automatically

  #### Describe how you would create a simple slideshow page.

  ```html
  <div class='slide-page'>...</div>
  <div class='slide-page'>...</div>
  <div class='slide-page'>...</div>
  ```

  ```css
  html, body, .slide-page {
    width: 100%;
    height: 100%;
  }

  .slide-page {
    position: fixed;
    top: 0;
    left: 0;
    display: none;
  }

  .slide-page:first-child {
    display: block;
  }
  ```

  ```js
  window.addEventListener('click', () => {
    document.querySelector('.slide-page').remove();
  });
  ```

  #### If you could master one technology this year, what would it be?

  Haskell. Haskell really helps developers a lot to perform much better, even
  though they don't really use Haskell directly because through learning Haskell,
  we can have better understand for other languages as well. It has been, and
  will be a well-designed language and many other languages have been adopting
  functional concepts from it and I would say it is fascinating and valuable
  language for every developer.

  #### Explain the importance of standards and standards bodies.

  Standards describe how a thing does and should work. It is extremely
  important especially in software, because the *thing* can be used by many
  people for different perposes. For example, there are several engines for
  JavaScript including V8, JavaScriptCore, Rhino, etc, and if there is no
  standard for the language, developers and users cannot feel ensured when doing
  something with it.

  Standards bodies, in the same manner, do a key role to form a standards and
  are essential in everywhere including both software and hardware.

  #### What is Flash of Unstyled Content? How do you avoid FOUC?

  It is caused when content is loaded before styles are applied to the content.
  It happens when style tags are placed after other content, or applied
  asynchronously, for example, by scripts.

  To avoid FOUC, the styles should be placed in order that they can be loaded
  and applied in the same rendering process as HTML elements do. The easiest way
  is to place them in the `head`, and avoid applying styles by scripts at the
  first load.

  #### Explain what ARIA and screenreaders are, and how to make a website accessible.

  They are for accessibility. To make a website accessible, we should try to
  follow the usage of HTML elements, for example, `h1` for headers and `section`
  for sections. Also it's good to take care of using visual contents, such as
  not forgetting to add an `alt` attribute to `img` tags.

  #### Explain some of the pros and cons for CSS animations versus JavaScript animations.

  ###### CSS animations
  - **pros**: They use GPU, so they are CPU-efficient. Don't consume JavaScript
    event loops.
  - **cons**: Hard to handle, as CSS doesn't contain logics. Not supported in
    old browsers.

  ###### JavaScript animations

  Opposite to CSS animations

  #### What does CORS stand for and what issue does it address?

  CORS stands for cross-origin resource sharing. There could be situation where
  some resources should be allowed from sources having different origin. CORS
  is a standard to enable cross-site HTTP requests for:

  - AJAX API call
  - Web Fonts
  - WebGL textures
  - Image/video frames drawn to a canvas using drawImage
  - Stylesheets
  - Scripts


  # HTML Questions

  #### What does a `doctype` do?

  It specifies which markup standard the page is using. With the information, the
  browser determines how to render the page according to the page's source code.

  #### What's the difference between standards mode and quirks mode?

  They are modes used by browser rendering engines. In the standards mode, the
  engine will render a page as HTML and CSS specifications specify. The quirks
  mode is to render legacy pages written before these standards are fixed. The
  legacy pages contain non-standard behaviours emulated in old browsers such as
  Internet Explorer 5 or Navigator 4.

  We can enforce browsers to use standards mode with a `<!DOCTYPE html>` tag.

  #### What's the difference between HTML and XHTML?

  *Not answered yet*

  #### Are there any problems with serving pages as `application/xhtml+xml`?

  IE < 8 will show a download dialog for the pages, instead of rendering them
  properly.

  #### How do you serve a page with content in multiple languages?

  Use `lang` (or `xml:lang` for XHTML) in tags. Also metadata and
  `Content-Language` HTTP header can be used.

  #### What kind of things must you be wary of when design or developing for multilingual sites?

  - `hreflang` attr in link
  - `dir` attr indicating language direction, such as `rtl`
  - `<meta charset='UTF-8'>`
  - `font-size` for `:lang({language_code})` selectors in CSS
  - difference in word langth for each language

  #### What are `data-` attributes good for?

  It makes HTML elements contain extra information without using non-standard
  attributes, or other hacks like that.

  #### Consider HTML5 as an open web platform. What are the building blocks of HTML5?

  *Not answered yet*

  #### Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.

  *Not answered yet*

  #### Describe the difference between `<script>`, `<script async>` and `<script defer>`.

  - `<script>` stops rendering process, and download and run a script.
  - `<script async>` don't stop rendering process while asynchronously
    downloading a script. When finishing download, it stops rendering and runs the
    script.
  - `<script defer>` don't stop rendering process while asynchronously
    downloading a script. When finishing rendering, it runs the script.

  #### Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?

  *Not answered yet*

  #### What is progressive rendering?

  When a HTTP response is flushed multiple times, a browser doesn't wait until
  the whole content is loaded and renders each part earlier.

  #### Have you used different HTML templating languages before?

  Yes. Jinja2 and Django template language in Python. Jade and EJS in JavaScript.
  Some more in other languages.

  # CSS Questions

  #### What is the difference between classes and ID's in CSS?

  *Not answered yet*

  #### What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?

  - Resetting: Remove all the native styles provided by browsers
  - Normalizing: Make the browser styles consistent

  #### Describe Floats and how they work.

  There are `left`, `right` and `none` for `float`. Each value indicates how an
  element should float. When `float` is set, each element will get out of its
  normal flow and will be shifted to the specified direction, until it gets its
  container or another floated element.

  #### Describe z-index and how stacking context is formed.

  `z-index` tells how elements should be stacked in a screen. Stacking context
  can be formed in several situations, but most famously, by a root element and
  positioned elements. In each stacking context, `z-index` will be calculated
  separately for its children and will stack the children in ascending order.

  #### Describe BFC(Block Formatting Context) and how it works.

  BFC is a part of rendering a webpage. It's used to determine from which
  positioning and clearing should be done. The context is created by several
  ways, but the most famously, by a root element, float, positioned elements.

  #### What are the various clearing techniques and which is appropriate for what context?

  ```css
  clear:both;
  ```

  ```css
  overflow: hidden;
  height: auto;
  ```

  #### Explain CSS sprites, and how you would implement them on a page or site.

  CSS sprite is combining multiple images into a merged one image and use CSS to
  render each of them properly for each element.

  It's usually implemented using `background: url(...) x-axis y-axis;`, or
  both `background-image` and `background-position`.

  #### What are your favourite image replacement techniques and which do you use when?

  Image replacement technique is to replace a normal text element with an image.
  There are many methods such as H5BP and Scott Kellum, as suggested [here](https://css-tricks.com/the-image-replacement-museum/).

  My faviourite is H5BP, as it is the simplest and most intuitive one.

  #### How would you approach fixing browser-specific styling issues?

  *Not answered yet*

  #### How do you serve your pages for feature-constrained browsers?
  ###### What techniques/processes do you use?

  *Not answered yet*

  #### What are the different ways to visually hide content (and make it available only for screen readers)?

  *Not answered yet*

  #### Have you ever used a grid system, and if so, what do you prefer?

  Yes, but not so many. I prefer Bootstrap.

  #### Have you used or implemented media queries or mobile specific layouts/CSS?

  Yes.

  #### Are you familiar with styling SVG?

  *Not answered yet*

  #### How do you optimize your webpages for print?

  ```css
  @media print {
    ...
  }
  ```

  #### What are some of the "gotchas" for writing efficient CSS?

  Usually about CSS selectors.

  - Avoid key selector for large numbers of elements
  - Prefer class and ID selector to tag selector
  - Avoid redundant selectors
  - Care of batching

  #### What are the advantages/disadvantages of using CSS preprocessors?
  ###### Describe what you like and dislike about the CSS preprocessors you have used.

  *Not answered yet*

  #### How would you implement a web design comp that uses non-standard fonts?

  - `@font-face` to write my own `font-family`
  - `@import` to import prepared web font(e.g. Google Webfonts)

  #### Explain how a browser determines what elements match a CSS selector.

  - Reads right-to-left
    - Check matching elements for the key(right-most) selector
    - Check if the elements are matching parents for the next selectors

  #### Describe pseudo-elements and discuss what they are used for.

  It's to style a part of an element, like `::first-letter` or `::before`.

  They can be used to add a special symbol before a paragraph, change color of
  first character of a line, etc.

  #### Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.

  *Not answered yet*

  #### What does ```* { box-sizing: border-box; }``` do? What are its advantages?

  *Not answered yet*

  #### List as many values for the display property that you can remember.

  *Not answered yet*

  #### What's the difference between inline and inline-block?

  *Not answered yet*

  #### What's the difference between a relative, fixed, absolute and statically positioned element?

  *Not answered yet*

  #### The 'C' in CSS stands for Cascading.  How is priority determined in assigning styles (a few examples)?  How can you use this system to your advantage?

  CSS priority is determined by [specificity and inheritance](https://www.smashingmagazine.com/2010/04/css-specificity-and-inheritance/).

  - Specificity: ID > class, psuedo-class > element, psudo-element
  - Inheritence: specified value → computed value → used value → actual value

  #### What existing CSS frameworks have you used locally, or in production? How would you change/improve them?

  *Not answered yet*

  #### Have you played around with the new CSS Flexbox or Grid specs?

  Yes.

  - http://flexboxfroggy.com
  - https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties

  #### How is responsive design different from adaptive design?

  - Responsive: There is one basic layout, and it changes responsively to
    screen changes
  - Adaptive: For each possible screen size, there is a distinct layout.

  #### Have you ever worked with retina graphics? If so, when and what techniques did you use?

  ```css
  @media (-webkit-min-device-pixel-ratio: 1.25), (min-resolution: 120dpi) {
    ...
  }
  ```

  #### Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?

  *Not answered yet*


  # JS Questions

  #### Explain event delegation

  When an event is fired from an element, the event will be bubbled up to its
  parent nodes. However, the original element where the event occurs, called
  'target', stays the same in the event object. Using the `target` property, we
  can always keep tracking which element actually causes an event captured by
  its parent, and it can help use reduce the number of event handlers as we
  sometimes don't need to add event listeners for every element.

  #### Explain how `this` works in JavaScript

  *Not answered yet*

  #### Explain how prototypal inheritance works

  *Not answered yet*

  #### What do you think of AMD vs CommonJS?

  *Not answered yet*

  #### Explain why the following doesn't work as an IIFE: `function foo(){ }();`.

  *Not answered yet*

  ###### What needs to be changed to properly make it an IIFE?

  ```js
  (function foo() { })(); // or
  (function foo() { }());
  ```

  #### What's the difference between a variable that is: `null`, `undefined` or undeclared?
  ###### How would you go about checking for any of these states?

  *Not answered yet*

  #### What is a closure, and how/why would you use one?

  *Not answered yet*

  #### What's a typical use case for anonymous functions?

  *Not answered yet*

  #### How do you organize your code? (module pattern, classical inheritance?)

  *Not answered yet*

  #### What's the difference between host objects and native objects?

  - Host objects: what an environment(browser, Node.js, etc) provides
  - Native objects: what JavaScript provides


  #### Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?

  *Not answered yet*

  #### What's the difference between `.call` and `.apply`?

  *Not answered yet*

  #### Explain `Function.prototype.bind`.

  *Not answered yet*

  #### When would you use `document.write()`?

  When someone gives me one million dollar for doing it.

  #### What's the difference between feature detection, feature inference, and using the UA string?

  - Feature detection: directly check if a feature is implemented

  ```js
  if (Promise) {
    let a = Promise.resolve('hello');
  }
  ```

  - Feature inference: infer if a feature is implemented by checking other properties

  ```js
  if (MozSmsMessage) {
    // guess it must be Firefox...
  }
  ```

  - UA string: UA stands for UserAgent, which a browser natively exposes to
    scripts and HTTP header

  ```js
  console.log(navigator.userAgent); // "Mozilla/5.0 (Macintosh; ..."
  ```

  #### Explain AJAX in as much detail as possible.

  *Not answered yet*

  #### Explain how JSONP works (and how it's not really AJAX).

  A JSONP response contains a callback function usually written in JavaScript,
  and when the response is flushed, the callback will be launched. It's more like
  script tag injection, rather than AJAX.

  #### Have you ever used JavaScript templating?

  Yes.

  ###### If so, what libraries have you used?

  Handlebars, Mustache, etc.

  #### Explain "hoisting".

  *Not answered yet*

  #### Describe event bubbling.

  It's when an event is bubbled into container elements, in the higher level of a
  DOM tree.

  #### What's the difference between an "attribute" and a "property"?

  - Attribute: specified in HTML, always in the form of string
  - Property: specified in DOM object, can have any type of JavaScript

  #### Why is extending built-in JavaScript objects not a good idea?

  *Not answered yet*

  #### Difference between document load event and document ready event?

  - document ready: when a HTML document is loaded and rendered
  - document load: when a HTML document and assets in the document are all loaded
    and rendered

  #### What is the difference between `==` and `===`?

  *Not answered yet*

  #### Explain the same-origin policy with regards to JavaScript.

  Same-origin means having same host, port and protocol(HTTP or HTTPS). If a
  script in the different origin should be accessed, we can consider using CORS.

  #### Make this work:
  ```javascript
  duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
  ```

  ```js
  let duplicate = (arr) => arr.concat(arr);
  ```

  #### Why is it called a Ternary expression, what does the word "Ternary" indicate?

  *Not answered yet*

  #### What is `"use strict";`? what are the advantages and disadvantages to using it?

  Advantages

  - Cannot assign a value to an undefined global variable
  - Fire TypeError for not-allowed assignments
  - `this` in a normal function refers to `undefined`, instead of `global`

  In short, it secures JavaScript.

  Disadvantage

  - When using global strict mode and concatenating the script with other scripts
    not using strict mode, the other scripts can be broken.

  #### Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`

  *Not answered yet*

  #### Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?

  *Not answered yet*

  #### Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?

  *Not answered yet*

  #### Explain what a single page app is and how to make one SEO-friendly.

  *Not answered yet*

  #### What is the extent of your experience with Promises and/or their polyfills?

  *Not answered yet*

  #### What are the pros and cons of using Promises instead of callbacks?

  *Not answered yet*

  #### What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?

  *Not answered yet*

  #### What tools and techniques do you use debugging JavaScript code?

  *Not answered yet*

  #### What language constructions do you use for iterating over object properties and array items?

  *Not answered yet*

  #### Explain the difference between mutable and immutable objects.
  ###### What is an example of an immutable object in JavaScript?
  ###### What are the pros and cons of immutability?
  ###### How can you achieve immutability in your own code?

  *Not answered yet*

  #### Explain the difference between synchronous and asynchronous functions.

  *Not answered yet*

  #### What is event loop?
  ###### What is the difference between call stack and task queue?

  *Not answered yet*



  # Testing Questions

  #### What are some advantages/disadvantages to testing your code?

  ###### Advantages

  - Prevent regression errors
  - Ensure there is no missing part to change when refactoring
  - Tests can be used as specs
  - Test process can be shared amongst team members

  ###### Disadvantages: there are rarely disadvantages

  - It may or may not take more time to prototype.

  #### What tools would you use to test your code's functionality?

  For JavaScript, the basic `assert` module is quite enough for simple tests.
  But when it gets a big and production-level project, it is a better idea to
  set a test framework. For backend, I usually use Mocha. For frontend, Mocha
  can still be used with headless browsers such as PhantomJS. There are also
  other famous tools like Selenium for browser tests.

  #### What is the difference between a unit test and a functional/integration test?

  - A unit test is on a small unit and checks if each unit works well.
  - A functional test is on a particular feature and check if it generates a
    proper output for a provided input.
  - An integration test checks if each part(or unit) of code works well together
    and results in combination functions correctly.

  #### What is the purpose of a code style linting tool?

  It is to keep source codes in a repository consistent and easy to read. Linting
  also prevent possible mistakes developers can make. For example, some linter
  provides options to check which indentation should be used(it is not actually
  what a linter should do though). A linter can also check if there is any used
  variable which hasn't been declared, or if there is any unused variable. In
  short, linting is a kind of static analysis.

  # Performance Questions

  * What tools would you use to find a performance bug in your code?
  * What are some ways you may improve your website's scrolling performance?
  * Explain the difference between layout, painting and compositing.


  # Network Questions

  #### Traditionally, why has it been better to serve site assets from multiple domains?

  It's because browsers usually have limits on the number of concurrent downloads
  from a domain at a moment. So, serving assets from multiple domains can
  increase the concurrent level.

  #### Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.

  When I enter a website's URL, in the transport layer, it will ask a local DNS
  what is the IP of the provided URL. We know the IP of the local DNS server by
  the DHCP protocol, when a node connects to internet and gets an IP address.

  After that, a browser will try to establish a TCP connection with a server
  having the retrieved IP by 3-way handshake. When it establish a TCP connection,
  the browser will form an HTTP request containing an HTTP header and body.

  After the HTTP request is sent and the server responds with an HTTP response,
  the browser will parse the HTTP response header and body, and will render the
  website. If the document contains additional assets, the browser will create
  HTTP requests for the assets and send them like above.

  * What are the differences between Long-Polling, Websockets and Server-Sent Events?
  * Explain the following request and response headers:
    * Diff. between Expires, Date, Age and If-Modified-...
    * Do Not Track
    * Cache-Control
    * Transfer-Encoding
    * ETag
    * X-Frame-Options
  * What are HTTP actions? List all HTTP actions that you know, and explain them.


  # Coding Questions

  #### *Question: What is the value of `foo`?*
  ```javascript
  var foo = 10 + '20';
  ```

  *Answer:* `'1020'`, because of type coercion from Number to String

  #### *Question: How would you make this work?*
  ```javascript
  add(2, 5); // 7
  add(2)(5); // 7
  ```

  *Answer:* A general solution for any number of parameters
  ```js
  'use strict';

  let sum = (arr) => arr.reduce((a, b) => a + b);
  let addGenerator = (numArgs, prevArgs) => {
    return function () {
      let totalArgs = prevArgs.concat(Array.from(arguments));
      if (totalArgs.length === numArgs) {
        return sum(totalArgs);
      }
      return addGenerator(numArgs, totalArgs);
    };
  };

  let add = addGenerator(2, []);

  add(2, 5); // 7
  add(2)(5); // 7
  add()(2, 5); // 7
  add()(2)(5); // 7
  add()()(2)(5); // 7
  ```

  #### *Question: What value is returned from the following statement?*
  ```javascript
  "i'm a lasagna hog".split("").reverse().join("");
  ```

  *Answer:* It's actually a reverse method for a string - `'goh angasal a m\'i'`

  #### *Question: What is the value of `window.foo`?*
  ```javascript
  ( window.foo || ( window.foo = "bar" ) );
  ```

  *Answer:* Always `'bar'`

  #### *Question: What is the outcome of the two alerts below?*
  ```javascript
  var foo = "Hello";
  (function() {
    var bar = " World";
    alert(foo + bar);
  })();
  alert(foo + bar);
  ```

  *Answer:*
  - First: `Hello World`
  - Second: Throws an exception, `ReferenceError: bar is not defined`

  #### *Question: What is the value of `foo.length`?*
  ```javascript
  var foo = [];
  foo.push(1);
  foo.push(2);
  ```

  *Answer:* `.push` is mutable - `2`

  #### *Question: What is the value of `foo.x`?*
  ```javascript
  var foo = {n: 1};
  var bar = foo;
  foo.x = foo = {n: 2};
  ```

  *Answer:* `undefined`. Rather, `bar.x` is `{n: 2}`.

  `foo.x = foo = {n: 2}` is the same as `foo.x = (foo = {n: 2})`. It is because
  a left term is first referenced and then a right term is evaluated when an
  assignment is performed in JavaScript. When `foo.x` is referenced, it refers
  to an original object, `{n: 1}`. So, when the result of the right term, `{n:
  2}`, is evaluated, it will assigned to the original object, which is at the
  moment referenced by `bar`.

  #### *Question: What does the following code print?*
  ```javascript
  console.log('one');
  setTimeout(function() {
    console.log('two');
  }, 0);
  console.log('three');
  ```

  *Answer:* `one`, `three` and `two`. It's because `console.log('two');` will be
  invoked in the next event loop.


  # Fun Questions

  #### What's a cool project that you've recently worked on?

  [Pen](https://github.com/noraesae/pen).

  It is a markdown previewer written in JavaScript with realtime preview. The
  preview page is updated powered by VirtualDOM of React, which means that only
  modified parts in the original markdown are actually updated in the DOM tree of
  the preview page. It's super cool(at least I believe). If interested, please
  look into it :smile:

  #### What are some things you like about the developer tools you use?

  I personally use Tmux and Vim with several customisations. I especially
  recommend using [CtrlP](https://github.com/kien/ctrlp.vim) and
  [Syntastic](https://github.com/scrooloose/syntastic) for Vim.

  I won't describe them in detail here, but if you're using Vim, you must love
  them.

  #### Do you have any pet projects? What kind?

  Many. You can find them in [my GitHub page](https://github.com/noraesae).

  I like to write useful tools not only for developers, but for normal users.
  So many of my pet projects are about tools including markdown previewers,
  a input changer, etc. I also write some JavaScript packages as well.

  #### What's your favorite feature of Internet Explorer?

  What is Internet Explorer? Nevermind. I like the color of its logo.

  #### How do you like your coffee?

  I'm a fan of coffee. I usually drink cups of coffee a day, especially a working
  day.

  I also like to drink tea and beer :beer:


## License

[MIT](LICENSE.md)
