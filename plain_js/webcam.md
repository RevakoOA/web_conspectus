# Webcam stuffs

Get video from webcam:
```javascript
	function getVideo() {
		navigator.mediaDevices.getUserMedia({video : true, audio : false})
        .then(localMediaStream => {
            console.log(localMediaStream);
            video.src = window.URL.createObjectURL(localMediaStream);
            video.play();
        })
        .catch(err => {
            console.log(`OH NO!!!`, err);
        })
	}
```

To make some changes in what user is watching we need to populate that image on canvas.

```javascript
	function paintOnCanvas() {
		const width = video.videoWidth;
		const height = video.videoHeight;
		canvas.width = width;
		canvas.height = height;

		return setInterval(()=> {
        ctx.drawImage(video, 0, 0, width, height);
		}, 20);
	}
	
	video.addEventListener('canplay', paintOnCanvas);
```

To take photo from video streaming:

```javascript
function takePhoto() {
    snap.currentTime = 0;
    snap.play();

    const data = canvas.toDataURL('image/jpeg');
    const link = document.createElement('a');
    link.href = data;
    link.setAttribute('download', 'selfie');
    link.textContent = "Download Image";
    console.log(link);
    link.innerHTML = `<img src='${data}' alt="Pretty nice selfie"/>`;
	strip.insertBefore(link, strip.firstChild);
}
```

