![Tengu JS](https://raw.github.com/isaymatato/tengu/master/assets/logo.png)
========

General JS utility framework

[Wiki](https://github.com/isaymatato/tengu/wiki)

##Overview

###Installation

#####In node
Include the file tengu.js in your project's root directory

#####In the browser
Include the file tengu.js with a script tag in your HTML:

`<script src="tengu.js"></script>`

###Usage
```javascript
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
