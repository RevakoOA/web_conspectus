CSS Varaible
============

CSS varaibles are better than variables in SASS, because you can change them with JavaScript and if *.sass is compiled, you can't change anything in *.css

To declare css variable in *.css use '--' as a style to selector ':root'

Then you can use your variables in *.css. Example:
```bash
	:root {
		--zero-margin: 0px;
	}
	body {
		margin: var(--zero-margin);
	}

```

Selecting and changing CSS variables by JavaScript and input HTML tag
=====================================================================
```bash
<input type="range" name="variable" min="0" max="infinity" value="10" data-suffix="px">
```
data-* attribute is used to store some data in the HTML tags. In this example we store suffix 'px'

name attribute is used to store the name of the variable 
```bash
const suffix = this.dataset.suffix;
```
How to select a variable with JS? We have to select all document

```bash
document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
```