title: General Questions
---

* What did you learn yesterday/this week?
* What excites or interests you about coding?
  * Solving problems, can make some tasks more efficient and faster
* What is a recent technical challenge you experienced and how did you solve it?
* When building a new web site or maintaining one, can you explain some techniques you have used to increase performance?
  * Optimizing performance consists of many things to do. First consider using caching on resources that don’t change frequently. Use Gzip compression to reduce content size of Javascript, CSS and html files. Minimize Javascript and CSS files data. Use CDN for your javascript and CSS files. Reduce image sizes by cropping them. Optimize database queries by reducing the joins and using index of field that require search
  * If building a js framework website, when using react or library remove unused js code from js package; a lot them are just for development. Eliminate everything not going to be used
  * write optimal code, avoid making unnecessary REST calls
  * make your website a progressive web app
  * use compression; and easier to transmit the to the browser, trading dl speed for cpu usage used to uncompress the content

* Can you describe some SEO best practices or techniques you have used lately?
  * have self described url names
  * have good content which allows google to put you higher in searches
  * add site types in header of html

* Can you explain any common techniques or recent issues solved in regards to front-end security?
  * 2 areas of fes: avoiding security code that deals with accessing attacks, avoid a suer able to execute malicious code from browser. Prevention:put filter in forms; etc validation, also can be done on server. Can use heaeders that only access specific websites from js, so a hacker can’t inject server code from a nonwhitelisted server. Csrf and wtf form security, use a csrf form token(it’s part of the session), every form generates a new one, and only that specific browser that got the html of the form can send post requests
  * user validation, block them with forbidden msg
 
* What actions have you personally taken on recent projects to increase maintainability of your code?
  * Split codes in files, and file name describing code.
  * To increase a project's maintainability: Following clean code practices. Keep classes/methods small.
* Talk about your preferred development environment.
   
* Which version control systems are you familiar with?
  * GitHub, Git
* Can you describe your workflow when you create a web page?
  *  Start w/design(visual design), create grid, create interactive elements
* If you have 5 different stylesheets, how would you best integrate them into the site?
  *  compile them into one document if possible. It is easier for a client to load one file vs five. But  keep the precompiled files separate for better code maintainability and organization.
  * in a given page only include the style sheet for that given page and don’t load them every page in your app/site(also true for script/js files)

* Can you describe the difference between progressive enhancement and graceful degradation?
  * look up; both aspects work to solve problem when it’s visited by old and new machines
  * you have your core website, then falls back to a simpler version if the browser is older
  * progressive enhancement- additional features unlock based on browser/machine capabilities
  * graceful deg- e.g. if your browser doesn’t have js installed, display html with no js functionality
* How would you optimize a website's assets/resources?
  * should always have optimal size(ex msg or images)
  * have image rules, to ensure images have best rez but does not stall your user’s experience

* How many resources will a browser download from a given domain at a time?
  * 	As many as the browser will accept, no defined limit
  * 	Most browsers have 6 as a limit

    * What are the exceptions?
      * -	Depends on the size of assets, e.x. images (?look up more)
* Name 3 ways to decrease page load (perceived or actual load time).
  * load one part of the given component of a page, and not every single piece
  * Minimize stuff to load just to what the user sees, other stuff (lazily loading; etc twtr/linkedin stuff only loads when you scroll) items loaded via promises and loaded later
  * Caching, ex website that doesn’t change dynamically, can put server in front or have caching embedded; instead of going to server, a specific page is stored in memory on client’s browser/pc, or a specific server/intermediate server if not found in the cache
  *	Use a CDN, ex have one for different regions depending on where a user lives, so there aren’t timeouts	

* If you jumped on a project and they used tabs and you used spaces, what would you do?
  *	Config your dev env, to use an indentation style
* Describe how you would create a simple slideshow page.
  * Design the html, have some html component that can be manipulated, and show a different image everytime, use javascript to change the image every set amount of time
  * In html, load all slides you want to show, then have one show, all else hidden, then have a button, that hides one then shows the other, maybe add fading when a button is clicked for a visual effect, implement the hiding/fading with javascript DOM manipulation

* If you could master one technology this year, what would it be?
  * 
* Explain the importance of standards and standards bodies.
  * -w3c, internet is open/free but there are org that have built the internet over decades and decides the different stds that should be followed
	-they have access/security/other stds
  -ex all images have some text, some pages can be converted to voice to expanded web accessibility to others
	-lets everyone have similar user experiences
  -when making an app or program, helps things be compatible with different computers/browsers or later versions in time

* What is Flash of Unstyled Content? How do you avoid FOUC?
  * A flash of unstyled content (FOUC, also flash of unstyled text) is an instance where a web page appears briefly with the browser's default styles prior to loading an external CSS stylesheet, due to the web browser engine rendering the page before all information is retrieved.
  Avoid by:
  -	Keeping your css small and fragmented
  -	Display an initial loading animation so a user won’t see something unstyled
  -	Progressive enhancement, load a base page for a user additional interactive elements

* Explain what ARIA and screenreaders are, and how to make a website accessible.
  * -Accessible Rich Internet Applications (ARIA) is a set of attributes that define ways to make web content and web applications (especially those developed with JavaScript) more accessible to people with disabilities.
  It supplements HTML so that interactions and widgets commonly used in applications can be passed to assistive technologies when there is not otherwise a mechanism. For example, ARIA enables accessible navigation landmarks in HTML4, JavaScript widgets, form hints and error messages, live content updates, and more.
  -https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA

* Explain some of the pros and cons for CSS animations versus JavaScript animations.
  * -	CSS animations: maybe faster
  -	JS=code execution, so browser is better@ interpreting CSS, some things you can’t do in CSS; ex more complex animations you need to implement in JS(maybe give example)

* What does CORS stand for and what issue does it address?
  * -Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any other origins (domain, scheme, or port) than its own from which a browser should permit loading of resources. CORS also relies on a mechanism by which browsers make a “preflight” request to the server hosting the cross-origin resource, in order to check that the server will permit the actual request. In that preflight, the browser sends headers that indicate the HTTP method and headers that will be used in the actual request.
  https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

* How did you handle a disagreement with your boss or your collaborator?
* What resources do you use to learn about the latest in front end development and design?
  * JavaScript Weekly, CSS Weekly, HTML5 Weekly and Node Weekly. 
  * Meetup groups

* What skills are needed to be a good front-end developer?
  * HTML, CSS, JavaScript. A frontend developer needs to be fluent in these three languages
  * Knowledge of CSS and JavaScript frameworks.
  * CSS preprocessors
  * Version control and other developer tools.
  * Responsive design.
  * Testing.
  * Web performance/building and automation tools.

* What role do you see yourself?
* Explain the difference between cookies, session storage, and local storage?
  * LocalStorage
    localStorage is a way to store data on the client’s computer. It allows the saving of key/value pairs in a web browser and it stores data with no expiration date. localStorage can only be accessed via JavaScript, and HTML5. However, the user has the ability to clear the browser data/cache to erase all localStorage data.
    Session storage
    •	stores data only for a session, meaning that the data is stored until the browser (or tab) is closed
    •	data is never transferred to the server
    •	can only be read on client-side
    •	storage limit is about 5-10MB
    •	opening multiple tabs/windows with the same URL creates sessionStorage for each tab/window

    Cookie
    •	Stores data that has to be sent back to the server with subsequent XHR requests. Its expiration varies based on the type and the expiration duration can be set from either server-side or client-side .
    •	Cookies are primarily for server-side reading (can also be read on client-side), localStorage and sessionStorage can only be read on client-side.
    •	Size must be less than 4KB.

    https://krishankantsinghal.medium.com/local-storage-vs-session-storage-vs-cookie-22655ff75a8



    https://www.cram.com/flashcards/front-end-developer-questions-7529950


