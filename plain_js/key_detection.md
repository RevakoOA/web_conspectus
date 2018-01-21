# Key detection

The logic is all in code. The main point is keeping pressed buffer small.
Thus we should cut it after ~~secretCode~~ length is achieved.

```javascript  
  const pressed = [];
  const secretCode = 'dixit';
  window.addEventListener('keyup', e => {
      const key = e.key;
      if (key.length === 1) {
          pressed.push(key);
      }
      pressed.splice(0, pressed.length - secretCode.length);
      if (pressed.join("").includes(secretCode)) {
          console.log("You got this!!!");
      }
     console.log(pressed);
  });
```