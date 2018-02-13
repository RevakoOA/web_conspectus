Drag to Scroll

Actually this is a mouse event. If mousepressed and mousemoved we should scroll div horizontally. It's just a combination of the mouseleave, mouseup and other events
We need to registrate if on how many pixels we moved our mouse on the X axis and also is moudepressed or not.

```bash
<script>
    const sloder = document.querySelecto('.items);
    let isDown = false;
    let startX;
    let scrollLeft;

    slider.addEventListener ('mousedown', () => {
        isDown = true;
        slider.classList.add('active');
        //console.log(e.pageX);
        startX = e.pageX - slider.offsetLeft;
        let scrollLeft = slider.scrollLeft;
        
    });
     slider.addEventListener ('mouseleave', () => {
         isDown = false;
         slider.classList.remove('active');
    });
     slider.addEventListener ('mouseup', () => {
         isDown = false;
         slider.classList.remove('active');
    });
     slider.addEventListener ('mousmove', () => {
        if(!isDown) return; // stop the fn running
        //console.count(isDown);
        //console.log(startX);
        e.preventDefault();
        const x = e.pageX - slider.offsetLeft;
        const walk = (x - startX) * 3; //this is going to tell how far we moved mouse from intial place
        slider.scrollLeft = walk;
    });
    
</script>
```