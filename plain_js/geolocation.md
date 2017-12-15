Geolocation
===========

Access to the geo location in possible only in secure origin.
Localhost is secure origin or it can be https protocol.

You can access to all that you want to know: location, direction and speed.

```bash
	navigator.geolocation.watchPosition((data)=>{
		console.log(data);
    }, error => {
        console.err("Error!!!");
    }); // for continues looking
	navigator.geolocation.getCurrentPosition() // for one time info
```

In response you will get timestamp and object Position with all you need. 
accuracy field means meters.
direction field means degree clockwise from North.
speed in km/h.
Some data can be null.


