# Udacity FEND-Project: Website Performance Optimization

## Some general things

### How to run
You can clone the repository and run the index.html file or you can just [click this link](https://derrado.github.io/fend-website_optimization/)

### Used build tools
No build tools were used, minifiy and image-optim through online services

## Part 1: Optimize PageSpeed Insights score for index.html

### Important
* The HTML wasn't minified on purpose :)
* The images could have been encoded and inlined to reduce request, size went up for about 30%, and since page speed was well under 1s, decided against it

### Modified Images
* Created new (smaller and/or optimized) images for all images on the starting page

### Modified HTML
* Changed the img sources to the new and location (img/)
* Changed google-font to load async via JS and moved to the bottom of the body tag
* Inlined the minified normal css
* Added media print to specific print stylesheet
* Moved Javascript to the end of the body tag
* Set loading of http://www.google-analytics.com/analytics.js to async

## Part 2: Optimize Frames per Second in pizza.html

### Modified JS (main.js)
Listed below are the main changes in the file
#### EventListener Scroll
* Function now calls updatePositions() via rAF

#### EventListener DomContentLoaded
* Reduced number of floating pizzas to 40, which results in 5 rows of pizzas drawn
* Removed height and width on elem-creation (obsolete after image-resize and css-style fix)
* Changed image to the new, smaller version
* Set floating_pizzas variable once, holds all .mover divs

#### Function updatePositions()
* Moved calls to document.body.scrollTop out of the loop
* Pizzas now move through translateX instead of style.left

### Images
* Created new (smaller) image for the floating pizzas, so the browser has no need to resize them

### CSS
* Added will-change: transform; to .mover
* Reduzed width to 100px in .mover

## Part 3: Changing Pizza-Sizes in under <5ms

### Modified JS (main.js)
The only function changed was resizePizzas(), mainly all calls to offsetWidth an other expensive calls have been seperated out of the loops and put in seperate variables at the top of the function.
* determineDx() was stripped down to functional calls


