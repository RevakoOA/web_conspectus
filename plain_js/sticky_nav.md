# Sticky navigation panel

```javascript
  const nav = document.querySelector('#main');
  const topOfNav = nav.offsetTop;

  function fixNav() {
    if (window.scrollY >= topOfNav) {
        document.body.classList.add('fixed-nav');
        document.body.style.paddingTop = nav.offsetHeight + 'px'; // after nav fixed, it doesn't use space in document
    } else {
        document.body.style.paddingTop = '0px';
        document.body.classList.remove('fixed-nav');
    }
  }

  window.addEventListener('scroll', fixNav);
```

