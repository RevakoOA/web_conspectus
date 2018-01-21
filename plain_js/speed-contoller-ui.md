Video Speed Controller UI
=========================

A lot of developers like to watch videos at faster speed rate from 1.5x to 2.0x, so we will use our new custom input element to control speed of the video

```bash
//html code:
<div class="speed">
	<div class="speed-bar"></div>
</div>
js code:
const speed = document.querySelector('.speed');
const bar = speed.querySelector('.speed-bar');
const video = document.video;

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
````
