# Local storage
Local storage is Map<String, String>.
```javascript
	// on start of script
	const items = JSON.parse(localStorage.getItem('items')) || [];
	
	// on each update
	localStorage.setItem('items', JSON.stringify(items));
```