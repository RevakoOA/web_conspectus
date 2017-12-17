Native Speech Recognition
=========================

We have SpeechRecognition - it's a global variable that lives in the browser. In Chrome it lives in webkit so to choose this variable for all browsers use the following code

```bash
window.SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition; 
```  

Now we have to create variable in which we will store our SpeechRecognition object

```bash
	const recognition = new SpeechRecognition();

	recognition.addEventListener('result', e => {
		console.log(e);
	});

	recognition.start();
```

To display words we have to make an array from our variable and also join it

```bash
	recognition.addEventListener('result', e => {
		const transcript = Array.from(e.results)
			.map(result => result[0])
			.map(result => result.transcript)
			.join('')
	});

	document.createElement('p').textContent = transcript; //The result will be displayed in p tag in *.html file
```