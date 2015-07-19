## Website Performance Optimization portfolio project

Part 1 - index.html - Mobile portfolio
======================================
*Requirements- Web browser that is capable of running HTML, javascript and CSS

*How to run- Begin by opening the index.html file in your web browser.

	For the first part of this project I optimized the critical rendering path on the mobile portfolio (index.html) and obtained a PageSpeed score of 95 for mobile and 96 for desktop. 

	The following optimizations were made on index.html
		-removed the font link. It didn't look like it was a special font so would be better not spend the time loading.
		-Media type was changed to print on the CSS for print media. This way it is not render blocking
		-Moved the css for screen inline in the index.html. This saves time by not needing to put out a request for a separate file.
		-Set google analytics script as async so it is not part of critical rendering path
		-Optimized and compressed images, made pizzeria.jpg a thumbnail at the size the HTML actually displays it at.
		-minified index.html (non-minified filename: index.nonMin.html)


Part 2 - views/pizza.html - Cam's Pizzeria
==========================================
*Requirements- Web browser that is capable of running HTML, javascript and CSS

*How to run- Begin by opening the views/pizza.html file in your web browser.

	For the second part of this project I used the Chrome Developer tools to analyze and optimize the JavaScript code to acheive a frame rate of 60 FPS on the pizza.html and main.js files.

	The following adjustments were made to optimize this page in pizza.html, main.js and style.css.

		pizza size slider 
			-I removed determinDX() function. I incorporated its functionality into changeSlider() where it returns a pizza size as "small", "medium" and "large" (line 411). These were added as classes to the CSS file. Each class had the appropriate width as a percentage.
			-changePizzaSizes() was modified to no longer use document.querySelectorAll . Instead it uses document.getElementsByClassName and this was moved outside the loop so it no longer needs to call it each cycle. ChangePizzaSizes now changes sizes by assigning a CSS class. (line 436)
			-added "will-change: transform;" to CSS for .randomPizzaContainer to get the browser to render as a separate layer.

		Pizza animation on scroll 
			-Reduced the number of pizzas to 30 and rows to 6 (line 519 and 527 in main.js)
			-modified updatePositions() so checks scrollTop just once instead of each time through the loop (line 490 in main.js)
			-added "will-change: transform;" to CSS for .mover
			-changed querySelectorAll to getElementsByClassName (line 493)
			-position pizzas using CSS transform instead of style.left (line 500)
			-select #movingPizzas1 using getElementByID instead of querySelector. Also moved this outside of the loop so it 
			only calls it once. (line 524)
