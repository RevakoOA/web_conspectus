```javascript
  
  const hero = document.querySelector('.hero');
  const heroText = document.querySelector('h1');

  const maxShadowStep = 100;
  function shadowUpdate(e) {
      const {offsetWidth : width, offsetHeight: height} = hero; // nice way to gather some important fields in one line
      let {offsetX: x, offsetY: y} = e; // here x = e.offsetX, and y = e.offsetY
      if (this !== e.target) { // target is disassembled further
          x += e.target.offsetLeft;
          y += e.target.offsetTop;
      }
      let shadowStepX = Math.round(maxShadowStep * (this.offsetWidth / 2 - x)/this.offsetWidth);
      let shadowStepY = Math.round(maxShadowStep * (this.offsetHeight / 2 - y)/this.offsetHeight);
	  // nice way to make style
      heroText.style.textShadow = `
         ${shadowStepX}px ${shadowStepY}px 0 rgba(255,255,0,6),
         ${shadowStepX * -1}px ${shadowStepY}px 0 rgba(255,0,255,0.8)
      `;
  }
  hero.addEventListener('mousemove', shadowUpdate, true);
```

## Target
target field store the element which is the most top and which mouse is exactly point to.
e.offsetX and e.offsetY are showing where the mouse pointer is relatively to target left-top corner.