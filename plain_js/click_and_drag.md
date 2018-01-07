# Click and drag objects on page

What we need for modeling such behavior are:
 * Listeners
	* mousedown
	* mouseup
	* mouseleave
	* mousemove
 * Variables
	* boolean mouseDown
	* double startPosition (for x or y)
	* double alreadyScrolled
	
```javascript
	const dragable = document.querySelector('.list_items');
	let alreadyScrolled;
	let mouseDown;
	let startX;
	dragable.addEventListener('mousedown', (e) => {
		mouseDown = true;
		startX = e.screenX;
		alreadyScrolled = dragable.scrollLeft;
	});
	
	dragable.addEventListener('mouseup', (e) => {
		mouseDown = false;
	});
	
	dragable.addEventListener('mouseleave', (e) => {
		mouseDown = false;
	});
	
	dragable.addEventListener('mousemove', (e) => {
		if (!mouseDown) return;
		const momentX = e.screenX;
		const step = (momentX - startX);
		dragable.scrollLeft = alreadyScrolled - step;
	});
```
