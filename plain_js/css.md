```css
<style>
    :root {
        --base: yellow;
        --spacing: 10px;
        --blur: 10px;
    }
	 img {
        padding: var(--spacing);
        background: var(--base);
        filter: blur(var(--blur));
    }
</style>
```
:root - pseudoclass that points to root element of document, 
usefull for creating custom variables here

All custom variables should start with '--'

After that they can be used with ```var(--custom_name)```

After changing the UI update is automatic.

To change property in JS:
```javascript
	const suffix = this.dataset.sizing || ''; // in case of 'px' or something
	document.documentElement.style.setProperty(`--${custom_name}`, this.value + suffix);
```
