---
title: "Web Controlled Arduino LED"
date: 2020-08-15T16:31:15+05:30
draft: false
---
As part of my initial experiments with the Arduino, I've been playing around with the [Johnny-Five library](http://johnny-five.io/). One of these led to building a homegrown room-temperature sensor + GraphQL project about which I wrote in my workplace [blog](https://hasura.io/blog/experiments-with-arduino-and-hasura/).

Another low-hanging fruit is a setup to control Arduino LEDs from the browser, through a HTML page with buttons. That is what this post is about. I'll split this post into three parts:
1. The browser
2. The server
3. The Arduino board

### The Browser
This is a very simple HTML page, with `on` and `off` buttons. Their `onclick` events are hooked up to a couple of JS functions.
   ```
      <button onclick="makeBlink()">Blink LED</button>
      <button onclick="stopBlink()">Stop LED</button>

  ```

### The server
Since the Arduino is being controlled by Nodejs and Johnny-Five, we use Express to route the button onclick events.
  ```
    app.get('/blink', (req, res) => {
          res.send("Hellow world!")
          blink()
    })
    app.get('/stopblink', (req, res) => {
        res.send("Bye!!")
        stopblink()

    })
    app.listen(3000, () => {
        console.log("Server has started and is listening on port 3000")
    })
  ```

### The Arduino board
##### Initial Board setup
- [Download](https://www.arduino.cc/en/Main/Software) the Arduino IDE for your machine and install it
- Connect your Arduino board to your machine and open up the IDE
- Navigate to File -> Examples -> Firmata -> StandardFirmataPlus
- This would open a “sketch” in the IDE. Load this on to the board
I have a simple LED pin connected to port 13 on the board.
##### On board ready
Once the board is detected by Johnny-five and initialized, `board.on("ready")` is available. The `blink()` and `stopblink()` functions within this are called from the `/blink` and `/stopblink` routes that we have setup above.

### Running the project
The full code is [here](https://github.com/meerasndr/arduino-webcontrolled-led).  Once all the packages are installed, run `node server.js`. This should setup a localhost on port 3000, which is ready to listen to incoming requests.
Open up `pressbtn.html` in your favourite browser. If everything is set up correctly, clicking on the Blink LED and Stop LED buttons should control the on-board LED.
