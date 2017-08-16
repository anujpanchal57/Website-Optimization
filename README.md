# Website Performance Optimization Project

To install the project on your machine, you can either clone the repository using git, or click the download zip button on the right and unzip the file.

To view theoptimized webpage, double-click on index.html or go to (https://anujpanchal57.github.io/Website-Optimization/).

> I've optimized `index.html` page to achieve at least a 90 PageSpeed score.
> I've optimized the JavaScript in `pizza.html` to achieve a frame rate of **60fps** when we scroll.
> I've also reduced the amount of time to resize pizzas in `pizza.html` to as much as less than **5 ms**.

### Part 1: Optimizing the PageSpeed Insights score for `index.html`
In this part, I've performed the required operations in `index.html` in order to optimize the PageSpeed Insights Score to atleast 90.

#### Optimizations performed:
* Reduced the size of image `pizzaria.jpg` to 100px width
* Inline the CSS in `css/style.css` in `index.html`
* Make the google-analytics script async
* Added a media query for `print.css`
* Use the Web Font Loader to load the Google WebFont
* Minify CSS
* Compress jpg and png files

##### Sources:
* https://github.com/typekit/webfontloader
* https://cssminifier.com/


### Part 2: Optimizing the Frames per Second in `pizza.html`
I've optimized the speed of fps in this section

#### Optimizations performed:
* Moved all the constants outside the for loop in `updatePositions`
* Moved the `Math.sin` calculation outside the for loop in `updatePositions`
* Moved `var items = document.getElementsByClassName('mover');` to anonymous function to the bottom of the file to stop `updatePositions` from re-defining items on each and every scroll event
* Used `window.items[i].style.left = items[i].basicLeft + 100 * phase + 'px';` instead of using only `items`
* Set the number of pizzas equal to 36 in `document.addEventListener('DOMContentLoaded', function())`
* Replaced `querySelector` by `getElementById in document.getElementById("movingPizzas1").appendChild(elem);`
* Switched to `document.getElementById` in place of `document.querySelector` in the function `determineDx`
* Declared the `var phase` outside the for loop to prevent it from being created for each and every iteration
* Declared the `var elem` outside the loop to prevent it from being created for every iteration
* Declared the `movingPizzas` outside the for loop to prevent a DOM call on each and every iteration
* Changed CSS for `.mover: Add transform: translateZ(0);` to `will-change: transform; transform translate3d(0,0,0);` and also `backface-visibility: hidden;`
* Used `transform` instead of `window.items[i].style.left = items[i].basicLeft + 100 * phase + 'px';`
* Replaced the `animationReady` to check with the updatePositions in this event listener: `window.addEventListener('scroll', updatePositions);`
* Calculated number of pizzas based on the respective window size


##### Sources:
* https://github.com/marc1981/optimization/tree/master/views/js
* https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById
* https://github.com/uncleoptimus/udacityP4/blob/gh-pages/views/js/main.js

### Part 3: Optimizing the Time to Resize Pizzas in `pizza.html`
I've optimized the `pizza.html` and `main.js` to achieve the minimal time required.

#### Optimizations performed:
* Modified the `changePizzaSizes` in the following ways:
* Moved the `document.document.querySelectorAll(".randomPizzaContainer");` outside for loop
* Refactored inorder to use a switch to set pizza width to avoid Forced Synchronous Layout and avoid use of `determineDx` to determine the new pizza widths
* Switched to `document.getElementsByClassName` from `document.querySelectorAll` in the line of `changePizzaSizes`
* Shifted `randomPizzas.length` to a local variable so, that the array's length property should not be accessed on every iteration
* Shifted `var pizzasDiv = document.getElementById("randomPizzas");` outside the for loop so, the loop only makes a single DOM call
* Changed the CSS for `.randomPizzaContainer: Add transform: translateZ(0);` and `will-change: transform;`

##### Sources:
* https://www.w3schools.com/jsref/met_document_getelementsbyclassname.asp
* https://stackoverflow.com/questions/3808808/how-to-get-element-by-class-in-javascript
