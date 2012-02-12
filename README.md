#jQuery Conf UK notes.
##10th Feb 2012
_hashtag #jquk, twitter @jquk_

###Jack Franklin
@Jack_Franklin


Just my notes from the jQuery UK Conf 2012. On Github, in Markdown, like a proper geek should, live blogged by commiting & pushing changes to Github. Fuck yeah developers.

If you've got any extra things I missed, feel free to fork, add & pull request.


#General Things that have popped up that I want to check out
- kendoUI
- backbone.js, ember.js

---

#Todd Parker
##jQuery Mobile

@toddmparker

http://jquerymobile.com/

https://github.com/jquery/jquery-mobile

Filament Group

contains UI tools & Ajax page transitions
1 codebase for all platforms

###Quick Start Guide
1. Make an actual proper website (HTML 5 doctype)
2. Add jQuery Mobile (include jQuery mobile theme, jQuery core, jQuery mobile)
3. Set viewport tag `<meta name="viewport" content="width=device-width,initial-scale=1">`
4. Automagic stuff:
   ajaxify links + forms = transitions
   enhance all form elements
   wrap contents in a 'page' container

###data-role HTML5 attribute
- uses classes like "button", etc to define types 
- `data-role="listview"` adds list styles for you

For accessibility, always add labels but hide them if you don't want them - don't just don't add them!

###page regions
`data-role="header"` (footer/content/header) _not required, all optional_

###mega api
big API for developers

###coming soon in jQuery Mobile (1.1 ish)
- new loader design
- transition re-vamps and new types
- Android 2.x (and a couple of others) struggle with transforms, more basic browsers default to just having a fade transitions if they can't manage anything more.
- chrome coming to Android which is good news
- true fixed toolbars, now more browsers support `position: fixed;` and with __native__ scrolling
- forms in fixed toolbars
- forms: `data-mini="true"` (new set of minature form elements), made for sitting in a toolbar
- you can use `data-enhance="false"` or `data-ajax="false"` to tell jQuery mobile to keep its hands off (useful for 3rd party stuff on the page)
- fix a horrible iOS orientation bug via JS (Apple haven't done it for 2 years)
- AMD
- download builder
- taking a step back & fix bugs

###1.2 stuff
- exposing things (like popups) that are used internally but not available via API
- Fetchlinks (coming in 1.2), taking navigation model & exposing it.
- overflow regions
- responsive layouts

###Resources
http://codiqa.com/ for prototyping

jQM works with Backbone & sorts

Lots of books available

All collected at http://jquerymobile.com/resources


Use http://jquerymobile.com/test to play

Can always use more help so get in touch

Stay in the loop:
- jquerymobile.com/blog
- @jquerymobile

Slides; http://speakerdeck.com/u/toddparker/p/jquery-mobile-keynote-uk-conference

---

#Web vs Apps
##Dion Almaer and Ben Galbraith
@dalmaer & @bgalbs

Microsoft said at IE9:

> "With HTML5, you can make __as rich an experience as an app__"

> "HTML5 is a __beautiful thing__. You get lost in the experience and forget that you are on the web"

People using mobile apps more and more (and in some cases even more than websites on a day to day basis)

Now days it's very easy to install new software compared to in the past

Native & Platform both have big advantages.

Continuous delpoyment much easier on web than via an App Store

Released Thorax, built on Backbone, Underscore, Lumbar, etc: http://walmartlabs.github.com/thorax/

---

#Pitfalls and opportunities of single page applications
##Jorn Zaefferer
@bassistance
https://github.com/jzaefferer

(does QUnit - need to check that out) https://github.com/jquery/qunit

###Building single page apps
- static files & JSON API
- no page reloads
- Backbone.js, ember, whatever
- simple applications architecture
- better user experience
- super frameworks to help out

###Pitfalls & potential solutions

###Better user experience?
####urls not changing on link clicks
- urls don't change when page changes - can't bookmark, link, etc, or opening in new window doesn't work
- use HTML5 __history API__ (no support in IE < 10 - surprised?, Opera < 11.5, Safari < 5 ), need to use fallbacks

####HTML history API

- `history.pushState()`
- `history.replaceState()`
- `document.addEventListener("popstate", callback, false) //not quite consistent - use library to work around`

####HTML history libraries
- history.js
- Backbone.history.start()
- simple-history.js

###Github repo for code examples: https://github.com/jzaefferer/pitfalls-examples

server side rendering: node.js

###What could go wrong?
- in space no one can hear you scream
- in browsers no one can hear your code scream 

###Error handling
- catch on client & send to server
- aggregate errors

####Error Types
- SyntaxError (silly) only likely during testing
- TypeError
- Ajax

to catch errors you can bind to the window's `error` event

```
window.onerror = function(message, file, line) {}
```

```
$(document).ajaxError(function(event, xhr, options, error) {}
```

####Aggregation Options
- custom
- analytics tool
- airbrake, bugsense

whatever you do, catch them all!

###Is it worth the trouble?
- better UX
- good first impression
- stable product


---

#QUnit
##Laurent Delcambre
@tquila_laurent

###Why use Unit tests
- check business logic validity
- repeating tests easily
- detecting regressions
- ease cross browser testing
- siwtching from bottom-up to top-down
- business logic in the front end
- TDD is awesome

###Steps to use QUnit

####Set up HTML structure to display results

```css
#qunit-header /* name of test suite */
#qunit-banner /* show up red / green if test fail / pass */
#qunit-userAgent /* show uA */
#quinit-tests /*container for test results */
```

####Asserting Results
```js
ok(boolean [,message]);
test("ok test", function() {
  ok(true, "ok succeeds");
  ok(false, "ok fails");
});
```

```js
equals(actual, expected [,message]);
```


`same` is the better version of `equals`, it uses `===` and compares content of objects
```js
same(actual, expected [,message]);
```

####Testing Asynchronous Callbacks
problem: don't wait for the result of the asynchronous operations
solution: call `stop()` before any asynchronous operation, call `start()` after all assertions are done, which means test runner can continue

###Perspectives
BDD: Behaviour Driven Development
- Jasmine
- Screw.unit
- JSpec

check out phantom.js for command line testing


---

#Christian Heilmann
##Embracing & Celebrating Redundancy
@codepo8
Slides: http://icant.co.uk/talks/jquk/

###Bad browsers gave us a few options
- cater to the lowest common denominator?
- block out old browsers?
- abstract browser differences into a library?

###jQuery chose the third option
- created an API to work around browser differences
- introduced chaining
- replace the DOM
- access everything with CSS selectors (Sizzle)

###jQuery simulates the browser we wanted
- specialised for content maniplation
- easy interface effects and animations
- easier event handling
- Ajax without the X 

###Abstraction != Obstruction (going over the top)
we keep abstracting on abstractions and this is __BAD__ (lots of things do this)

###Imagine...
- if browsers didn't suck anymore
- and what if that has actually happened?
- jQuery won, it showed a better way
- and now it's time to reap the rewards, __change to the native web tech__
- we should give Microsoft a chance again

There's a backlash! `"\\".replace('s','')`

Remember that events _bubble up (since IE5!)_, so delegate!

Stop changing CSS with jQuery, leaves a __tight bond between struct & behav__. It's presentation on the behaviour layer.

`document.querySelector` is `$`

Don't do an `onclick` handler on a form - use the `submit` event so it works with keyboards 

`preventDefault` exists in native JS

Assign event listeners to parent and check if the element you're interacting with is what you want:
```js
someVar.addEventListener('click', function(e) {
  var t = e.target;
  if(t.tagName === "LI") { ... }
});
```

(Example of todo list & all the corresponding code is in the slides (linked to above))

###Techniques to write less
- delegate, don't loop
- add classes to CSS
- fancy stuff in CSS, not JS

Start sites with sensible HTML structures. Think about it!

###Trickery for Small Code
- semantic HTML
- animations & transitions with CSS - smooth! (hardware accelerated)
- reusing variables (using a URL hash as ID, etc)

###Christian's Wishes 
- use what browsers natively give you
- plan and architect solutions, don't pile effect on effect
- structure your code in cached elements and reusable functions
- __don't answer any JS questions with use jQuery__
- don't write plugins for edge cases (this is nearly PHP land)
- use what browsers have and give browsers feedback. Fix source, don't abstract.

---

#Haymo Meran
##Aloha Editor
@draftkraft
http://aloha-editor.org/

> Aloha Editor makes contnet in your browser editable

`$(#editable).aloha()`

Edit the web - like MS Word 

WYSIWYGs are supposed to show __SIMILAR__ but most just suck

Uses `contenteditable` (HTML attribute)

Issues with it as the standard wasn't defined, each browser does it differently. So Aloha was made to solve these issues and make a cross browser editor.

jQuery UI captures mouse events (draggables) so sometimes it gets in the way with Aloha. To solve, add a `handle` to each draggable (or whatever)

check out http://aloha-wikidocs.com for real time collaboration - looks awesome.

---

#Paul Irish
##Webapp Development Stack & Tooling
@paul_irish

- We all want rich web apps, responsive, fast, fun & good experiences
- Development is focused lots on common tasks rather than being what's unique to the on eproject
- We want to stop doing common tasks and build fun stuff

Hixie live dom viewer http://software.hixie.ch/utilities/js/live-dom-viewer/

###What is frontend tooling?
Optional software that assists in development of web apps.

###The Webapp Lifecycle - tooling contexualised
- boilerplate
- authoring abstractions
- frameworks
- iteration workflow
- performance tuning
- build & optimization
- deploy

####Boilerplate
- blueprint, html5bp, mobile boilerplate

####Authoring Abstractions

#####CSS
- sass, less, compass (sits ontop of sass)
- less = nieve version of sass
- stylus (another layer on top of sass, looks good)

#####Markup
- HAML
- Markdown
- jade
- handlebars

#####Scripting
- coffeescript "think in JS but type less"
- TameJS
- dart


####Frameworks & The Application Stack

TodoMVC - shows a simple todo app in lots of JS frameworks https://github.com/addyosmani/todomvc http://addyosmani.github.com/todomvc/

__You need tools to support your stack__

####Iteration Workflow

Iteration Automators
- good old terminal!
- LiveReload http://livereload.com
- CodeKit http://incident57.com/codekit
- auto save JS & CSS changes to Chrome dev tools with plugin (DevTools Autosave 0.2.2 https://github.com/NV/chrome-devtools-autosave)

####Editors & IDES

- lots of options, irrelevant which one you use, just __LEARN IT__

####Browser Dev Tools (Chrome)
_get chrome canaray for new stuff_
- can now override user agent in Chrome Dev tools
- can dock to right of screen

- use closure compiler to minify everything down, this also creates a sourcemap json file
- prettyprint in dev tools helps but doesn't rename short variables
- "enable source maps" in Chrome Dev tools uses the sourcemap file closure creates and shows you the original JS. Fuck yeah.
- can debug on android devices with toolkit on your laptop. Note to self: buy an Android phone!

####JSHint / JSLint
- hook it up with your editor to give you JS help & feedback

Slides: http://dl.dropbox.com/u/39519/talks/jquk-tooling%2Bappstack/index.html

---

#Large Scale Applications Development with jQuery & JavaScript
##Addy Osmani
@addyosmani

###Basic Concepts

####Decoupling

- separates unit of code that don't depend on each other
- break a large module down into lots of smaller pieces and then you can reuse them.
- reduce the risk of brekaage when other modules fail
- use pub/sub

####Pub/Sub
- logically decouple objects generating events
- from those reacting to them
#####Ways of doing them
- jQuery custom events
```js
$(document).trigger('eventName');
$(document).on('eventName', function() {})
```
- Ben Alman's wrapper (on the slides)
- some more options (on the slides)


####Potential Problems
- if one part of your application breaks, can the app fix this break itself?
- how much of what we create is easily reusable
- can our models be tested independently
- how secure is your application from itself
Work arounds coming up!

###Patterns

_code in slides_

####Facade Pattern
- simplifies a module through a simple API that is exposed to the public, with complexity hidden behind
- hides implementation level details

####Mediator Pattern
- analogy: air traffic control:
- tower handles what places can take off or land
- all communication done from planes to tower
- centralised controller
- pub/sub via a centralised mediator, event driven
- as calls pass through, it can perform validation and much more

###Modules
- AMD
- module pattern
- object literals

###Large Applications
- difficult to define
- most of manipulation & display falls to browser

####What are we looking for?
- loosely coupled architecture
- smaller independent modules
- flexibility to change

####Modules
- notify when something happens
- don't touch what they don't have to
- can't stop entire app from working

###Solution: Mix of Everything!

####Application Core
- manages the module lifecycle, starts, stops, restarts if necessary
- reacts to actions passed back from a sandbox (facade), handles logic
- enable adding & removing modules without causing breaks
- handles error detection and management

####Sandbox
- abstraction of the core that's an API for common tasks, used by modules
- interface for ensuring modules don't directly access the core & libraries
- permissions manager, securing what modules can/can't access

####Modules

- unique (__independent__) blocks
- initialize & destroy functions
- initialize can subscribe to notifications

github repo for the demo: https://github.com/addyosmani/largescale-demo

---

#Contextual jQuery
##Doug Neiner
@dougneiner

Approaches to jQuery:

###Declarative

- repeated code
- heavy use of IDs
- changes to HTML require changes to JS (vice-versa)
- lots going on document ready

###Dynamic

- heavy use of classes, simple selectors
- delegated events sometimes
- less repeated code
- changes to HTML requires changes to jQuery
- lots on document ready

###Contextual

- minimal use of IDs, some classes
- leverages selectors & traversing
- very little repeated code
- HTML follows convention so edits require less changes to JS
- virtually nothing on document ready

###Benefits of Contextual jQuery

- flexible & more responsible code
- focussed
- less code overall
- easier to maintain & reuse

###Implementation

####Minimise Setup

- use `no-js` / `js` class on body
- use CSS to control state
- use modernizr!
- do what modernizr does for your own thing. Add CSS classes like `signed-in`, etc. Show / Hide / Traverse gets moved out of JS and into CSS

#####Just in Time Initialization

- set up areas of your page only when needed
- leverage user actions or probable actions as indiciation of what to initialise
- click, mouseenter, mouseleave, scrolling, focusin/focusout


####Delegated Events

- can be setup as soon as the context element is ready (when `document` is ready, so pretty much all the time, don't need to use `$(document).ready()`


####Traversal, Filters & Selectors

- brittle vs flexible traversal
- eg use `closest` rather than `parent` 
- not always needed to write the fastest code possible, often more maintainable code is better


####HTML Conventions

Conventions are patterns

- you can build them yourself
- need to be consisten
- a promise you make
- change between projects
- __have__ to work for you

Keep your markup clean
__think before you add markup to solve a JavaScript problem__

Always use `$(this).attr("href")` as jQuery normalises & fixes cross browser



###Write code like you spend money!
- opt to pay a little more later so you don't risk losing it all on something that never happens

###Write code like you buy a car!
- always weigh the difference between cost and quality

###Write code like you ask for directions or building something! 
- try to get there on your own first!

Slides: www.bit.ly/contextual-uk

---




---
