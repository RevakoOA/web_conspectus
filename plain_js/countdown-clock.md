Countdown Clock (Timer)
=======================
The main concepts of this lesson are:
	Date.now()
	new Date
	timestamp
	Learning how to convert miliseconds to h:m:s format

We are going to create a timer. That's why we have to work with time. To understand how to work with it we have to understand such thing as the timestamp which is time written in miliseconds from the 1 January 1970.

To get time at this moment we can use:

const now = Date.now();

To get our timer work we have to transform the timestamp into seconds and minutes and also call the function every one second by the setInterval function.

```bash
function timer(seconds) {
	const now = Date.now();
	const then = now + seconds * 1000; //We multiplying our seconds on 1000 to get them in milliseconds
}
```

Then we get our setInterval function and there we have to stop it when variable secondsLeft is less than 0

```bash
countdown = setInterval(() => {
	const secondsLeft = Math.round((then - Date.now()) / 1000);
	//check if we should stop it
	if(secondsLeft <= 0) {
		clearInterval(countdown);
		return;
	}
	// display it
	displayFunction(secondsLeft)
}, 1000);

function displayFunction(seconds) {
	concole.log(seconds)	
} // also we have to call this funciton as soon as th e function timer is invoked as we want to see our seconds value exactly when we reassign it.
```

So this is the main function of timer. Now we have to improve our displayFunction and also pass a seconds to the minutes. 

```bash
function displayFunction(seconds) {
	const minutes = Math.floor(seconds / 60);
	const remainderSeconds = seconds % 60;
	const display = `${minutes}:${remainderSeconds < 10 ? '0' : ''}${remainderSeconds}`;
	someH1tag.textContent = display;	
}
```



