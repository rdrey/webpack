# example.js

``` javascript
var a = require("./a");

// get module id
var aId = require.resolve("./a.js");

// clear module in require.cache
delete require.cache[aId];

// require module again, it should be reexecuted
var a2 = require("./a");

// vertify it
if(a == a2) throw new Error("Cache clear failed :(");
```

# a.js


``` javascript
module.exports = Math.random();
```

# js/output.js

``` javascript
/******/(function(modules) {
/******/	var installedModules = {};
/******/	function require(moduleId) {
/******/		if(typeof moduleId !== "number") throw new Error("Cannot find module '"+moduleId+"'");
/******/		if(installedModules[moduleId])
/******/			return installedModules[moduleId].exports;
/******/		var module = installedModules[moduleId] = {
/******/			exports: {},
/******/			id: moduleId,
/******/			loaded: false
/******/		};
/******/		modules[moduleId](module, module.exports, require);
/******/		module.loaded = true;
/******/		return module.exports;
/******/	}
/******/	require.e = function(chunkId, callback) {
/******/		callback(require);
/******/	};
/******/	require.modules = modules;
/******/	require.cache = installedModules;
/******/	return require(0);
/******/})
/******/({c:"",
/******/0: function(module, exports, require) {

/*** .\example.js ***/

var a = require(/* ./a */1);

// get module id
var aId = (/* ./a.js */1);

// clear module in require.cache
delete require.cache[aId];

// require module again, it should be reexecuted
var a2 = require(/* ./a */1);

// vertify it
if(a == a2) throw new Error("Cache clear failed :(");

/******/},
/******/
/******/1: function(module, exports, require) {

/*** .\a.js ***/

module.exports = Math.random();

/******/}
/******/})
```

# Info

## Uncompressed

```
Hash: a17a8967ca2bfedfb9b56d043420c318
Compile Time: 22ms
Chunks: 1
Modules: 2
Modules including duplicates: 2
Modules first chunk: 2
main   output.js:     1332 chars/bytes

 <id>    <size>  <filename>
       <reason> from <filename>
output.js
    0       295  .\example.js
       main
    1        31  .\a.js
       require (2x) from .\example.js
       require (1x) from .\example.js
```

## Minimized (uglify-js, no zip)

```
Hash: dd19a31556f41b87caf32b874541c423
Compile Time: 91ms
Chunks: 1
Modules: 2
Modules including duplicates: 2
Modules first chunk: 2
main   output.js:      442 chars/bytes

 <id>    <size>  <filename>
       <reason> from <filename>
output.js
    0       116  .\example.js
       main
    1        28  .\a.js
       require (2x) from .\example.js
       require (1x) from .\example.js
```
