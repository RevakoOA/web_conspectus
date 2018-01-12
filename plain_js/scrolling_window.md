# Scrolling

Very important stuff in listening for some events in case where events are too often 
is function debounce. Which will handle update only after some silent time.

```javascript
	function debounce(func, immediate = true, wait = 50) {
      let timeout;
      return function() {
        let context = this, args = arguments;
        let later = function() {
          timeout = null;
          if (!immediate) func.apply(context, args);
        };
        let callNow = immediate && !timeout;
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
        if (callNow) func.apply(context, args);
      };
    }
```

# To know where the mouse are
 Relatively the topLeftCorner of ...
e.pageX(Y) - whole document even page was scrolled
e.clientX(Y) - viewport (part of the page that you can see)
e.screenX{Y} - physical screen.

# To know where UI elements are located
**From proto HTMLElement**
offsetHeight - Returns a double containing the height of an element, relative to the layout.
offsetLeft - Returns a double, the distance from this element's left border to its offsetParent's left border.
offsetParent - Returns an Element that is the element from which all offset calculations are currently computed.
offsetTop - Returns a double, the distance from this element's top border to its offsetParent's top border.
offsetWidth - Returns a double containing the width of an element, relative to the layout.

# To know what is showing
window.scrollY - how many pixels are scrolled from top of the document
window.innerHeight - height of the visible area