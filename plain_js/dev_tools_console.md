# Console

* console.log("Hello World");
* console.log(`Hello ${name}`);
* console.log('%c Big text', "font-size:50px;");
* console.info("You already know the answer.");
* console.warn("Warning");
* console.error("Error");
* console.assert(1 === 1, "Test is failed");
* console.clear();
* ```javascript
	console.groupCollapsed(`${person.name}`);
       console.log(`This is ${person.name}`);
       console.log(`He is ${person.age} years old`);
       console.groupEnd(`${person.name}`);
```
* console.count('Method is called');
* ```javascript
	console.time('method name');
	method();
	console.timeEnd('method name');
```
* console.table(object_to_show);