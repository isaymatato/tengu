![Tengu JS](https://raw.github.com/isaymatato/tengu/master/assets/logo.png)
========

General JS utility framework

##Overview

###Installation

#####In node
Include the file tengu.js in your project's root directory

#####In the browser
Include the file tengu.js with a script tag in your HTML:

`<script src="tengu.js"></script>`

###Usage
```
var Tengu = require('./tengu.js'); // this line is not needed in the browser

Tengu(function(T) {
	//Call Tengu functions using 'T'
	//Example:
	var rbool = T.randomBool();
});
```

Alternatively, specific modules may be loaded from the constructor call:
```
//List the required modules as arguments, with the callback as the final argument
Tengu('util','debug','random',function(T) {
});

//Or list required modules as an array, with the callback as the final argument
Tengu(['util','debug','random'],function(T) {
});
```

###Modules
List of currently available modules:

*afk
*appcache
*canvas
*canvasmanip
*cookie
*date
*debug
*dom
*draw
*fileio
*fingerprint
*fps
*fullscreen
*geoloc
*graph
*gui
*image
*imagedata
*math
*namegen
*physics
*random
*regression
*sparkline
*stream
*string
*tween
*util
*validation
*websocket
*webstorage
*webworker
*xhr



