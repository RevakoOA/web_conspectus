Article about how to highlight some text with the single element
================================================================

To highlight we need some element that we will use for the background highlighting.
For example, highlight text when the user is hover over the element.

1. Add element grammatically:
```bash
	const highlight = document.createElement('span');
	highlight.classList.add('highlight'); // in css for class highlight implement some style
	document.body.appendChild(highlight);
```

2. Add listener to all elements you are interested in:
```bash
	elems.forEach(elem => {
       elem.addEventListener('mouseover', hoverHighlight);
    });
```

3. Implement hover function:
```bash
	function hoverHighlight(e) {
		const boundaries = this.getBoundingClientRect();
		
		const highlightBounding = {
		    width: boundaries.width,
			height: boundaries.height,
			left: boundaries.left + window.scrollX,
			top: boundaries.top + window.scrollY
		};
		
		highlight.style.width = `${highlightBounding.width}px`;
		highlight.style.height = `${highlightBounding.height}px`;
		highlight.style.transform = `translate(${highlightBounding.left}px, ${highlightBounding.top}px)`;
	}
```