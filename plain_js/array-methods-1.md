Array Cardio 1 (Lesson 4)
=========================

In this lesson we will see some methods to work with arrays

1. array.filter()

The way how filter works is passing the function into it and this function is going to loop over every single item in the array. Then we can write something in the function. For example we want to filter cars from imaginary array cars which were produced before 1995.

const carsBefore1995 = cars.filter(car => {
	if(car.year <= 1995) {
	return true;
	}
}); // We will get all cars produced before 1995
// It can also be written like this:
const carsBefore1995 = cars.filter(car => (car.year <= 1995));

2. array.map()
Map takes inner array. It does something with that array and then returns a new array with the same length. It's like a factory machine which takes a row material and then produce some products.

So, we have an array with objects inside. And we want to take some new array with only two properties of objects. We do this with this code:

const newArray = array.map(item => `${item.prop1} ${item.prop2}`);

3. array.sort()
The way how sort works is it takes two items and then we ask to sort that items. One item gets 1 and another -1 and then JS sorts the array based on this imaginary values.

const ordered = array.sort(function(a, b) {
	id(a.prop1 > b.prop2) {
		retuen 1;
	} else {
		return -1;
	}
});
// OR it can be shorted with the arrow function and the ternary operator

const ordered2 = array.sort((a, b) => a.prop1 > b.prop2 ? 1 : -1);

4. array.reduce()

Reduce allow us to build on every single one. We don't need a loop for doing something with array items. For example add some property into variable total

const reduced = array.reduce((total, item) => {
	return total + item.prop1
}, 0);

5. Connecting map(), sort() and includes(). 
Task: create a new array from array where items will have some special part of string.

array
	.map(item => item.textContent)
	.filter(newItem => newItem.includes('somePartOfString'));

6. Sorting the items alphabetically. For example we have an array of people names and they are written in a string dividede by comma. We want to sort all names alphabetically in according to the lastnames.

people.sort((lastOne, nextOne) => {
	const [aLast, aFirst] = lastOne.split(','); //aLast and aFirst it's a lastname and a firstname of item
	const [bLast, bFirst] = nextOne.split(',');
	return aLast > bLast ? 1 : 1;
});

7. Reduce() is the most flexible mathod that we have. Now we will sort items of array togeteher if their contetn is the same

array.reduce(function(obj, item) {
	if(!obj[item]) {
		obj[item] = 0;
	}
	obj[item]++;
	return obj;
}, {}); //So we start with blank object and then increment it when we add some item there.
}); 
