#jQuery Conf UK notes
##10th Feb 2012
###Jack Franklin

Just my notes from the jQuery UK Conf 2012. On Github, in Markdown, like a proper geek should.


#General Things that have popped up that I want to check out
kendoUI
backbone.js, ember.js

---

#Todd Parker - jQuery Mobile
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
http://codiqa.com/for prototyping

jQM works with Backbone & sorts

Lots of books available

All collected at jquerymobile.com/resources


Use jquerymobile.com/test to play

Can always use more help so get in touch

Stay in the loop:
- jquerymobile.com/blog
- @jquerymobile

---

#Web vs Apps
##Dion Almaer and Ben Galbraith
@dalmaer & @bgalbs

Microsoft said at IE9:
>"With HTML5, you can make __as rich an experience as an app__"
>"HTML5 is a __beautiful thing__. You get lost in the experience and forget that you are on the web"

People using mobile apps more and more (and in some cases even more than websites on a day to day basis)

Now days it's very easy to install new software compared to in the past

Native & Platform both have big advantages.

Continuous delpoyment much easier on web than via an App Store

Released Thorax, built on Backbone, Underscore, Lumbar, etc: http://walmartlabs.github.com/thorax/


