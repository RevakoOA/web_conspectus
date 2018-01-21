Modules in Node.js
==================

Module is main building block in Node.js.
Node.js is so light because there are only a couple of blocks that included in.
You can very easy insert others blocks if you need it. And that small chunks of code often are maintained by community.
That's why such blocks are so bugless.

How to manage modules:
----------------------
Every .js file can be module.
One .js file will run as root - only it will have field 'parent' null. To run others files have to write 
```bash
	var anotherModule = require('module_name');
```

Make a note, that embedded modules have higher priority. Best solution is not call your module with such names.

All variables are local for their module.
Access to current module is via link named 'module';
To make some variables accessible from others:
```bash
	// in module
	var a = 5;
	
	function showA() {
		console.log(a);
	}
	// If the variable is global for project
	global.numeVar = a;
	global.nameFunc = showA;
	// after this code a and showA is accessible from all files via global object.
	
	// If the variable is need only as result from this module
	exports.nameVar = a;
	exports.nameFunc = showA;
	// after this require('module') will return module.exports for which 'exports' is alias.
```

How Node.js will search module:
----------------------------------
1. Check if the module is embedded in node.js
2. If module name started with '/' -> search in root of file system.
3. If module name started with '[.[.]]/' -> 
a) search by path for file
 -> file extension:
 js -> load js
 json -> return plain object
 node -> load binary node file
b) search by path for directory
 -> 
  if dir has package.json -> find field 'main' and run this file.
  if dir has index.js -> run it
4. Search dir 'node_modules' and try to find .js file there 
5. Error, module is not find

Note: All modules are stored by node.js and module will executed only once, after that require will return link on the same object that was loaded firstly.
Node will save the index to module at the moment the module is started to loading.

