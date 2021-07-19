# html questions

* What does a `doctype` do?

* How do you serve a page with content in multiple languages?
** Localization, maybe users cookie or browser saves lang info, frontend has template with keys in it, then info got an returns/renders UI for correct lang. have diff types of files for each lang. files loaded when app starts in memory. Usually implemented with a library like react
* What kind of things must you be wary of when designing or developing for multilingual sites?
** maybe certain lang have different linguistics, e.g. Hello User in lang1 might be 1 line but in russian maybe 2+ lines and bigger components, rendering in one language might     work but not in another
* What are `data-` attributes good for?
** Allowing storage of extra info on given DOM without having to write own classes or attributes
* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
** Since everyone can use it, building blocks are HTML, CSS, JS, interactive elements(e.g. vids), html5 has a lot of things to support a lot of common use cases, you'd have to else write JS for in the past; e.g. maybe you'd have to use flask or complete use JS for vids
** HTML5 might be now be able to run a complete app embedded in the browser (look up)
* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.

* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
** script async- deals with how script is evaluated, like a promise, will run async once it's loaded. script may be run AFTER the page has loaded
** defer- script runs AFTER the page has loaded

* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
**so they are more easily defined and loaded first
**exception: (look up)

* What is progressive rendering?
** Rending all critical components first, then streaming noncritical content to the client
** render layout of website, then fill in content; so you have first load of the page ASAP, esp important if the connection of the client is poor

* Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
** (look up) maybe helps something load faster depending on the client's connection
** can use dif images depending on if mobile or web app

* Have you used different HTML templating languages before?

* What is the difference between `canvas` and `svg`?
** svg = data format for rendering imgs in the web, you're taking a file and importing in an svg element; (look up)
** canvas = when you want to draw, and use js to do this

* What are empty elements in HTML?
** elements that can't have a child e.g. img, br, meta, src
