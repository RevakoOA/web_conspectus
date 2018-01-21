Tally String Times with Reduce

The main concept of this lesson is to get the data-attribute from long list. We do it in the list of videos with it's duration. The main aim is to get those seconds and to transform to total time in format hour:mins:secs like for example YouTube do when we open some playlist.

To do this we will simply use map() and reduce() array methods, we will make an array from the NodeList object. And we will do the format oh time from seconds.

const timeNods = document. querySelectorAll('[data-time]'); //if we select elements like this we can't use the array methods for it. It looks like an array, but it's not. The prototype __proto__ of this object is NodeList. We have to convert our NodeList to array. Then we can use map() method to it.

const timeNods = Array.from(document.querySelectorAll('[data-time]');
const seconds = timeNodes
.map(node => node.dataset.time)
.map(timeCode => {
	const [mins, secs] = timecode.split(':').map(parseFloat); // then we split mins and secs in our array. But that returns string, so we have to map over this array and parse it
	return (mins * 60) + secs; // we transform minutes to seconds and add get the full length in sec
})
	.reduce((total, vidSeconds) => 
		return total + vidSeconds
	)

	let secondsLeft = seconds;
	const hours = Math.floor(secondLeft / 3600);
	seconds = secondsLeft % 3600;