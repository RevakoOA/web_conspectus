# Some basics to work with video element
## Logic
```javascript

    function togglePlay() {
        const method = videoViewer.paused? 'play' : 'pause';
        videoViewer[method]();
    }
	videoViewer.addEventListener("click", togglePlay);
	
	
	function skip() {
        const secsToSkip = this.dataset.skip;
        videoViewer.currentTime += parseFloat(secsToSkip);
    }
	skippers.forEach(skipper => skipper.addEventListener("click", skip));
	
	
	function handleRangeUpdate() {
        videoViewer[this.name] = this.value;
    }
	sliders.forEach(slider => slider.addEventListener("change", handleRangeUpdate));
    sliders.forEach(slider => slider.addEventListener("mousemove", handleRangeUpdate));
	
	
	function scrub(e) {
        const part = e.offsetX / prgAll.clientWidth;
        console.log(`Prg is ${prgAll.clientWidth}, offset is ${e.offsetX}, part is ${part}`);
        videoViewer.currentTime = part * videoViewer.duration;
    }
	prgAll.addEventListener('click', scrub);
```

## UI update

```javascript
	function updatePlay() {
        const icon = this.paused ? '►' : '❚ ❚';
        btnPlay.textContent = icon;
    }
	videoViewer.addEventListener("play", updatePlay);
    videoViewer.addEventListener("pause", updatePlay);

    function handleProgress() {
        const percent = (videoViewer.currentTime / videoViewer.duration) * 100;
        prgFilled.style.flexBasis = `${percent}%`;
    }
	videoViewer.addEventListener("timeupdate", handleProgress);
	
```