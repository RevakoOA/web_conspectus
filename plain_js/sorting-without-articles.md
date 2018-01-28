Sorting Array
=============

Array.sort method is used here. But we need to sort array without the articles. Articles should'nt affect on the sorting. Typically we use this code to sort array alphabetically:

```bash
const sortedArray = array.sort(function (a, b) {
    if(a > b) {
        return 1;
    } else {
        return -1;
    }
});
```
But we need to delete articles before words. So we create a function to do that and modify our sort method with some ES6 syntax.

```bash
function strip(arrayItem) {
    return arrayItem.replace(/^(a |the |an)/i, '').trim();
}

const sortedArray = array.sort((a, b) => strip(a) > strip(b) ? 1 : -1);

document.querySelector('#showArray').innerHTML = sortedArray
    .map(band => `<li>${band}</li>`)
    .join('')
```