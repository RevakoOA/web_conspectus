Flex Panels Image Gallery

This effect doesn't include much JavaScript. The only thing you need to know is that we can use 'transitionend' event in the addEventListener to add out classes synchronously one after another not to mix our animated transitioned css properties.

If you are not familiar with flexbox properties here is the best article about flexboxes that i found: https://css-tricks.com/snippets/css/a-guide-to-flexbox/

So, in different classes we operate property flex-grow. By default we have flex-grow: 1, but if we add some class with flex-grow: 5 to some panel, then after adding that class this panel will take space exactly 4x more than default property. When we do a transtion to this class we can see it animated. Also we can add some cubic-bezier() function to the transition.

Also we have to admit that container .panels and items .panel are all with display: flex properties. We can operate all of them to center content with justify-content: center. So we have a lot of flexboxes nested. 

To hide some content we can use transform: translateY(-100%). Also we use some :first-child and :last-child pseudo-selectors that selects children of some selector.

To make our panel bigger we ```bash addEventListener('click', panel.classList.toggle('open'))```
When our class added we change the flex value and also change the font-size. After that we do the translateY of children. We do that as it was mentioned before with the event 'transitionend'. This event is the same as 'click' or 'mousemove' event so we can easily use it.

Conclusions: 1. Flex is really useful because it is responsive and we don't need to specify the width
2. 'transitoinend' is the same event as for example 'click'