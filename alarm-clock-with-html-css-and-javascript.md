# How to Create an Alarm Clock with HTML, CSS & JavaScript

In this tutorial, you’ll learn how to create a simple alarm clock using HTML, CSS, and JavaScript. This project will teach you about working with time, DOM manipulation, and event handling in JavaScript.

Let's get started! 🚀


### Overview

An alarm clock app shows the current time and allows the user to set an alarm. When the time reaches the set alarm time, a sound is triggered. Here’s a breakdown of the project components:

1. **HTML** for structure.
2. **CSS** for styling.
3. **JavaScript** to handle time and alarm functionality.

---
<iframe height="600" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/Sambit-Nanda/embed/XWvoVLK?default-tab=js%2Cresult&theme-id=dark" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/Sambit-Nanda/pen/XWvoVLK">
  Untitled</a> by Sambit Nanda (<a href="https://codepen.io/Sambit-Nanda">@Sambit-Nanda</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### HTML Structure

Let's start with the HTML structure, which includes elements for displaying the current time and setting the alarm.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Alarm Clock</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>Alarm Clock</h1>
    <div id="clock">00:00:00</div>
    <input type="time" id="alarm-time">
    <button id="set-alarm">Set Alarm</button>
    <p id="alarm-message"></p>
  </div>
  <script src="script.js"></script>
</body>
</html>
```

In this HTML, we have:

- A `<div id="clock">` to display the current time.
- An `<input type="time" id="alarm-time">` for selecting the alarm time.
- A `<button id="set-alarm">` to set the alarm.
- A `<p id="alarm-message">` to show alarm notifications.

---

### CSS Styling

Now, let's add some basic styling to make our clock look neat.

```css
/* style.css */

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(135deg, #4e54c8, #8f94fb);
}

.container {
  text-align: center;
  background: #fff;
  padding: 40px 30px;
  border-radius: 12px;
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.2);
  width: 350px;
}

h1 {
  color: #4e54c8;
  font-size: 1.8em;
  margin-bottom: 10px;
}

#clock {
  font-size: 3.2em;
  margin: 20px 0;
  color: #333;
  font-weight: bold;
}

#alarm-time {
  margin-top: 15px;
  padding: 12px 15px;
  font-size: 1em;
  border: 1px solid #ddd;
  border-radius: 8px;
  width: 100%;
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1);
  color: #4e54c8;
}

#set-alarm {
  margin-top: 20px;
  padding: 12px 20px;
  font-size: 1em;
  font-weight: bold;
  color: #fff;
  background: #4e54c8;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.3s;
}

#set-alarm:hover {
  background: #3a3f92;
}

#alarm-message {
  margin-top: 20px;
  color: #dc2626;
  font-weight: bold;
  font-size: 1.1em;
}
```

---

### JavaScript Logic

Now that we have the structure and styling in place, let's add functionality to set and trigger the alarm.

```javascript
// script.js

const clockDisplay = document.getElementById('clock');
const alarmTimeInput = document.getElementById('alarm-time');
const setAlarmButton = document.getElementById('set-alarm');
const alarmMessage = document.getElementById('alarm-message');

let alarmTime = null;
let alarmTimeout = null;

// Function to display current time
function updateClock() {
  const now = new Date();
  const hours = String(now.getHours()).padStart(2, '0');
  const minutes = String(now.getMinutes()).padStart(2, '0');
  const seconds = String(now.getSeconds()).padStart(2, '0');
  
  clockDisplay.textContent = `${hours}:${minutes}:${seconds}`;

  // Check if alarm time is reached
  if (alarmTime && `${hours}:${minutes}` === alarmTime) {
    triggerAlarm();
  }
}

// Function to trigger alarm
function triggerAlarm() {
  alarmMessage.textContent = 'Wake up! Alarm ringing!';
  alarmTimeout = setTimeout(() => {
    alarmMessage.textContent = '';
  }, 5000); // Clear message after 5 seconds
}

// Set alarm time
setAlarmButton.addEventListener('click', () => {
  alarmTime = alarmTimeInput.value;
  if (alarmTime) {
    alarmMessage.textContent = `Alarm set for ${alarmTime}`;
  }
});

// Update clock every second
setInterval(updateClock, 1000);
```

In the JavaScript code:

1. **updateClock()** updates the displayed time every second and checks if the alarm time is reached.
2. **triggerAlarm()** triggers the alarm message and clears it after 5 seconds.
3. **Event Listener** on the button to set the alarm time from the user’s input.

---

### Putting It All Together

To complete this project:

1. **Link the CSS** in your HTML.
2. **Add the JavaScript** at the end of your HTML file.
3. **Test it out** by setting an alarm time and watching it go off when the time is reached.

---

### Conclusion

You've now created a functional alarm clock using HTML, CSS, and JavaScript! This project is a great example of using JavaScript for time-based applications and working with the DOM. 

---

