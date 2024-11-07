# QR Code Generator Using JavaScript & CSS

In this tutorial, you’ll learn how to build a **QR Code Generator** using JavaScript and CSS. QR codes are widely used in digital payments, product tracking, and more. This project will be simple yet effective, allowing you to input any text or link to generate a QR code instantly.

## Prerequisites
- Basic understanding of HTML, CSS, and JavaScript
- Familiarity with external JavaScript libraries

## Step 1: Basic Structure of the QR Code Generator

First, let’s set up the basic HTML and CSS for the QR code generator form. This includes an input box for URLs or text, a button to generate the QR code, and a display area for the QR code.

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>QR Code Generator</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="form">
    <h1>QR Code Generator</h1>
    <input type="url" id="website" name="website" placeholder="https://example.com" required />
    <div id="qrcode-container">
      <div id="qrcode" class="qrcode"></div>
    </div>
    <button type="button" onclick="generateQRCode()">Generate QR Code</button>
  </div>

  <script src="https://cdn.rawgit.com/davidshimjs/qrcodejs/gh-pages/qrcode.min.js"></script>
  <script src="script.js"></script>
</body>
</html>
```

### CSS (style.css)
```css
body {
  background: rgb(200, 220, 224);
  font-family: Helvetica, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.form {
  max-width: 400px;
  text-align: center;
  padding: 20px;
  background: #ffffff;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
}

.form h1 {
  background: #03773f;
  color: #fff;
  padding: 15px;
  margin: -20px -20px 20px;
  font-size: 25px;
}

.form input[type="url"] {
  width: 100%;
  padding: 10px;
  font-size: 17px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

.form input[type="url"]:focus {
  border-color: #5868bf;
  box-shadow: 0 0 5px #5868bf;
}

#qrcode-container {
  display: none;
}

.qrcode {
  padding: 16px;
  box-shadow: 0 0 10px rgba(67, 67, 68, 0.25);
  margin-bottom: 20px;
}

.form button {
  padding: 10px 20px;
  background: #0853b6;
  color: #fff;
  font-size: 17px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background 0.3s ease;
}

.form button:hover {
  background: rgba(88, 104, 191, 0.7);
}
```

## Step 2: JavaScript Functionality

Next, we’ll add JavaScript to handle the QR code generation. We’ll use the `qrcode.min.js` library to generate the QR code based on the URL or text input.

### JavaScript (script.js)
```javascript
function generateQRCode() {
  let website = document.getElementById("website").value;
  if (website) {
    let qrcodeContainer = document.getElementById("qrcode");
    qrcodeContainer.innerHTML = ""; // Clear previous QR code
    new QRCode(qrcodeContainer, website); // Generate new QR code
    document.getElementById("qrcode-container").style.display = "block";
  } else {
    alert("Please enter a valid URL");
  }
}
```

## How It Works
1. **Input Field**: Enter the URL or text you want to convert to a QR code in the input field.
2. **Generate Button**: Click the button, which calls the `generateQRCode` function.
3. **QR Code Display**: The QR code will be generated and displayed below the input field if the input is valid.

## Demo and Final Thoughts

This simple QR code generator project demonstrates how easily you can create a functional QR code tool using JavaScript and CSS. Try customizing the styles or adding features like error handling for non-URLs.

