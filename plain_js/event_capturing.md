Event capturing, Propagation, Bubbling
======================================

Bubbling
--------

In situation with nested divs what div will catch your click? - Actually all.

By default event going ripple down. From top to down. From the most nested to body and tab in browser.

To revert such logic (to go from down to top. From the tab in browser to the most nested element) use next code
``` bash
	divs.forEach(div => div.addEventListener('click', someFunc, {capture: true});
```
Propagation
-----------
To stop bubbling on the first element:
```bash
	function logE(e) {
		e.stopPropagation();
	}
	
	divs.forEach(div => div.addEventListener('click', logE);
```

To catch the click on the outermost element:
```bash
	function logE(e) {
		e.stopPropagation(); // stop on first triggered element
	}
	
	divs.forEach(div => div.addEventListener('click', logE, {capture: true}); // event will go from bottom to top if capture is true
```

Only for one click:
```bash
	divs.forEach(div => div.addEventListener('click', logE, {once : true}); // listener will unbind itself from the element after event emitted once
```

 