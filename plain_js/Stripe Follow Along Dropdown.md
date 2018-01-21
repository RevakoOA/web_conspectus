Stripe Follow Along Dropdown

To see how this effect works use this link https://stripe.com/ and move your mouse through the nav elements.

To make this effect we use one div tag that follows along the dropdown-div. Let's call it the background-div. If the dropdown-div is changed, this background-div change the size of itself appropriate to the content size in the dropdown-div.

We have to create 2 functions that will listen for mouseEntering and mouseLeaving form the nav element. Then we have to create event for all elemnts and pass that functions to listener for each element.

We show the content by simple adding the class to the element with this code:

```
setTimeout(() => this.classList.add('.className'), 150);
```
But to make the effect we use two properties in cSS: display: none/block and opcaity: 0/1. So, animation will be

That's how animation works either in React and ANgular. They just apply two separate classes when something enters or leaves

We have to measure the size of the content by JS.
It is made by method getBoundingClientRect(). This method makes an array in which we have width and height of the dropdown content div. Now we have to make background-div appropriate to the content size by the following code:

```
const dropdownCordinates = dropdown.getBoundingClientRect()
background-div.style.setProperty('width', `${dropdownCordinates.width}px`);
``` 
The same thing we have to do with height/top/left