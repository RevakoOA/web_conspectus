Stripe Follow Along Dropdown
============================

In the lesson 22 we saw how we can move a highlight appropriate to the mousemove.
Now we want to show a div that follows the mouse and it resizes all the time.
Today we are going to do the next step. It have the same idea as before.

So, the div that follows allong it's just one div that use different content.

Then we have a link and the dropdown that we want to show in the our dropdown-div.
So, when we move mouseout from the link, but we still on the div with content it should be showed. That wasnt' in the previous lesson 22 as there wasn't any div.

1. We take triggers - all our li elements and the dropdown-background also into variables.
2. Then we create 2 functionsand also make an events.
```bash
function handleEnter(){

}
function handleLeave(){
    
}

triggers.forEach(trigger => trigger.addEventListener('mouseenter', handleEnter));
triggers.forEach(trigger => trigger.addEventListener('mouseleave', handleLeave));
```
3. We get the content of the dropdown that we have to show.
    In the <li> item that we hover we want to fint it's content and display it.
    In the hanfelrEnter function:
```bash
function handleEnter(){
    this.classList.add('trigger-enter);
    setTimeout(() => this.classList.add('trigger-enter-active'), 150);
}
```
If we look through css we will fund that for hiding the elements we used opacity:0 adn display:none options. That's because we want to animate it. To make transition we will add another class: trigger-enter-active and now our content. This is done to show our content after small piece of time.
And in this class we change the opacity. First class will put display:block option and bg-div will be showed and adding of second class will show us the content.
That's how animation transtion works in the React and Angular. We just apply two separate classes when someone enters or leaves and then we use css to animate that.
4. Now we have to work with mouseleave function.
    We remove class when in the handleLeave function.
5. bg-div must be showed also in our functions.
```bash
unction handleEnter() {
    this.classList.add('trigger-enter');
    setTimeout(() => this.classList.contains('trigger-enter') && this.classList.add('trigger-enter-active'), 150);
    background.classList.add('open');
    };
```
Now, when .open is added to bg it showed, but we have to figure out how wide and how high and where on the page our bg should be showed.
6. We select dropdown and then do as in previous lesson .getBoundClientRect();
    We grab also the coordinates for the nav. Then we create an object with the coords and then we add style to the background variable.
```bash
function handleEnter() {
    this.classList.add('trigger-enter');
    setTimeout(() => this.classList.contains('trigger-enter') && this.classList.add('trigger-enter-active'), 150);
    background.classList.add('open');

    const dropdown = this.querySelector('.dropdown');
    const dropdownCoords = dropdown.getBoundingClientRect();
    const navCoords = nav.getBoundingClientRect();

    const coords = {
      height: dropdownCoords.height,
      width: dropdownCoords.width,
      top: dropdownCoords.top - navCoords.top,
      left: dropdownCoords.left - navCoords.left
    };

    background.style.setProperty('width', `${coords.width}px`);
    background.style.setProperty('height', `${coords.height}px`);
    background.style.setProperty('transform', `translate(${coords.left}px, ${coords.top}px)`);
  }
```
7. We also modify another function