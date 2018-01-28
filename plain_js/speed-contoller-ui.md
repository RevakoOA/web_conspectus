Video Speed Controller UI
=========================

A lot of developers like to watch videos at faster speed rate from 1.5x to 2.0x, so we will use our new custom input element to control speed of the video.

```bash
<video src="video-url"></video>
<div class="speed">
	<div class="speed-bar"></div>
</div>
```
So, in the beginning we have to select al of our elements and video

```bash
const speed = document.querySelector('.speed');
const bar = speed.querySelector('.speed-bar');
const video = document.video;
```
When we mouseover over the speed we want to change the height of the bar and also increase the speedrate of the video.  So we add eventlistener to speed and then we calculate height. We start calculating the Y point of the mousemove at the speed element. Zero point will be speed.offsetTop. 
Next step is to transform Y to percentage. We get the decimal fraction of the Y value of the speed element.
Then we define min and max. 
Then we transform decimal fraction to percentage. 
Then we style the height of nested element bar. As it is in percent it goes straight to the mouse. 
Now we want to make the texcontent of bar equal to the actual speed. We use our transform decimal fraction and then connect playback Rate of the video to our new variable playback.

```bash
speed.addEventListener('mousemove', (e) => {
	const y = e.pageY - this.offsetTop;
	const percent = y / this.offsetHeight;
	const min = 0.4; //min value in our input
	const max = 4; //max value in our input
	const height = Math.round(percent * 100) + '%';
	const playbackRate = percent * (max - min) + min;
	bar.style.height = height;
	bar.textContent = playbackRate.toFixed(2) + 'x';
	video.playbackRate = playbackRate;
});
```
