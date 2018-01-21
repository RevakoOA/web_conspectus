Ajax Type Ahead
=============== 

We are going to create a list of comething when we type something in the text input. Whatever we typed in we find the values. These values go from the external respurce by AJAX.

First thing that we need to do is to fetch that data from a *.json file. We need an empty array to put our list into.

```bash
const linkToFile = 'http://smth.smth/file.json'
let array = [];
```

When we just return an object with proto: Promise. That's why we have to work with it with function then() that returns a blob of data 
fetch(linkToFile).then(blob => console.log(blob))

Now the blob should be converted into *.json  

```bash
fetch(linkToFile)
	.then(blob => blob.json())
	.then(data => let = data))
```

// When we do this we get a massive array reassgined to the variable array that we created before.

Or if we want to be it a const we can push(data) ,but it will be nested into const. For this we can spread into it. The code we can use looks like this:

```bash
fetch(linkToFile)
	.then(blob => blob.json())
	.then(data => array.push(...data))
```

So this is the end of working with arrays. Now we need to find matches of what we type in the array. TO do this we create a function:

```bash
function findMatches(wordToMatch, array) {
	return array.filter(item => {
		const regex = new RegExp(wordToMatch, 'gi')
		return item.item2.match(regex) //that will look for string here. But the word string is not always. It should be variable worToMatch. How we can put a variable into a regular expression? We can't do it here, we create it outside. On the line before in the const regex/
	}) 
}
```
 
Function is done, now we have to display it. We do this with these code:

```bash
function displayMatches() {
  const matchArray = findMatches(this.value, array);
  const html = matchArray.map(place => {
    const regex = new RegExp(this.value, 'gi');
    const arrayItem = array.item.replace(regex, `<span class="hl">${this.value}</span>`);
    return `
      <li>
        <span class="name">${arrayItem}</span>
      </li>
    `;
  }).join('');
  suggestions.innerHTML = html;
}

const searchInput = document.querySelector('.search');
const suggestions = document.querySelector('.suggestions');

searchInput.addEventListener('change', displayMatches);
searchInput.addEventListener('keyup', displayMatches);
```