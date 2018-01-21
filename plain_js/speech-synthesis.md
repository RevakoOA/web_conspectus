Speech Synthesis (Lesson 23)
============================

It comes in most modern browsers. 

we create it with creating object.

const msg = new SpeechSynthesisUtterance();

msg.text = document.querySelector('[name="text"]).value

msg.text should be equal to the value of input

If we console.log our msg variable we will get an object with text fron the input, but with voice: null. That means that there is no voice set.

speechSynthesis is a global variable on which we can call method speak

speechSynthesis.speak(msg), but it still returns undefined as there still no voice.

We get voices (on Mac machine there are uch more then on Windows)

let voices = [];
voices = speechSynthesis.getVoices();

So we have our voices, by Default there is voice Alex(EN)
We can manipulate different properties of speechSynthesis, but the new thing in this lesson was event called 'voiceschanged' which is used only for this variable. When we do this event we can call some function in the addEventListener.