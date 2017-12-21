Sounds and animations
=====================

Sounds
------

To use sounds in js use in HTML
```bash
	<audio data-id="144" src="sounds/name.mp3"></audio>
```

Then in script we can do next:
```bash
	const audio = document.querySelector(`audio[data-key="${id}"]`);
	if (audio) {
		audio.currentTime = 0;
		audio.play();
	}
```

Animations
----------

To work with animation we need css class for animation:
```bash
	.in_animation {
		transform: scale(1.1);
		border-color: #00b3b3;
		box-shadow: 0 0 5rem #006666;
	}
```

Note: in base element class required :
```bash
  transition: all 1.0s ease;
```

In js after this:
```bash
function startAnimation() {
	key.classList.add('in_animation');
}

function endAnimation() {
	key.classList.remove('playing');
}
key.addEventListener('transitionend', endAnimation);
```