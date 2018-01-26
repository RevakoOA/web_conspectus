Sticky Nav
==========

This is really easy to do in jQuery, but we will do that in the ES6 od course.
1. We grab our nav that we want ot fix.
2. We create the eventListenet to the page and when we scroll we cakk function fixNav
3. We create our function fixNav
4. We calculate how far is nav from the top of the page. We create const topOfNav = nav.offsetTop
    !!!nav.offsetTop
5. In the function we look for topOfNov and if it is bigger then  nav.offsetTop we add new class and changes it style in the css.
6. But our nav jumps up when scroll. That's a problem.
7. We  have to add some padding when we do the fixed nav, because when nav becomes fixed body lose those pixels that were taken by it.
8. Than we manipulate logo if we want to. And the content.
The full code will look loke that:
```bash
<script>
    // Not a ton of code, but hard to
    const nav = document.querySelector('#main');
    let topOfNav = nav.offsetTop;

    function fixNav() {
      if(window.scrollY >= topOfNav) {
        document.body.style.paddingTop = nav.offsetHeight + 'px';
        document.body.classList.add('fixed-nav');
      } else {
        document.body.classList.remove('fixed-nav');
        document.body.style.paddingTop = 0;
      }
    }

    window.addEventListener('scroll', fixNav);

</script>
```