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

- afk
- appcache
- canvas
- canvasmanip
- cookie
- date
- debug
- dom
- draw
- fileio
- fingerprint
- fps
- fullscreen
- geoloc
- graph
- gui
- image
- imagedata
- math
- namegen
- physics
- random
- regression
- sparkline
- stream
- string
- tween
- util
- validation
- websocket
- webstorage
- webworker
- xhr



##Debug Module

###Methods:

**T.stackTrace()**

Returns the stack trace as an object.


**T.lineNumber()**

Returns the current line number in code.


**T.log(msg,[msgs])**

For now this just wraps console.log.  May add other features later.


**T.logMultiple(nTimesToLog, msg)**

Log message a fixed number of times (use in continuous loops to avoid msg spam)


Example:
```
for (i = 0; i < 100000000000000000000000000000000; i++) { 
    T.logMultiple(5,i);
}
```
Output will be:
0
1
2
3
4
(then stops, instead of logging a bazillion times)

**T.logOnce(msg,[msgs])**

Wraps console.log.  Works similar to 'logMultiple', but only logs once


**T.safeWrap(func, [onError], [onNotAFunc], [onFinally])**

Safely wrap a function with error callbacks

Set onNotAFunc to null to ignore


Basically this is a generalized error handler.  
*func* is the function you want to wrap (required)

*onError* is the error handler callback (optional)

*onNotAFunc* is an error handler that is called if *func* is not a function.  (optional - set to null to ignore)

*onFinally* is always called after everything (optional)


Example:
```
var f_error = function(){
	consol.elog('Hi!');
	//    ^ Whoopsie
}

var f_notAFunc = "I'm a string, not a function!";

var wrap_f_error = T.safeWrap( f_error, 
				function(e){
					console.log('We had an error!');
				}
			);
wrap_f_error();
//Output: 'We had an error!'

var wrap_f_notAFunc = T.safeWrap( f_notAFunc, 
				function(e){
					console.log('We had an error!');
				}
			);
wrap_f_notAFunc();
//Output: 'T.safeWrap: func is not a function, func: I'm a string, not a function!'

wrap_f_notAFunc = T.safeWrap( f_notAFunc, 
				function(e){
					console.log('We had an error!');
				},
				function(){
					console.log('Custom handler for not a function')
				}
			);
wrap_f_notAFunc();
//Output: 'Custom handler for not a function'

wrap_f_notAFunc = T.safeWrap( f_notAFunc, 
				function(e){
					console.log('We had an error!');
				},
				null
			);
wrap_f_notAFunc();
//No output, does nothing
```
