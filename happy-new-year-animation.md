# Happy New Year Animation | Pure CSS 🎆

Celebrate the New Year with a fun and vibrant animation crafted entirely with **HTML** and **CSS**! This project features a delightful "Happy New Year" greeting, animated balloons, fireworks, and a smooth transition into the year 2025.

Dive in to learn how to recreate this animation, and get inspired to add a touch of creativity to your web projects.

---

## 🎯 Features of the Animation
- **Text Animation:** Smooth transitions for the "Happy New Year" greeting and the changing year digits.
- **Balloon Movement:** A playful balloon animation that bobs and floats upwards.
- **Fireworks Display:** Dynamic and colorful fireworks that light up the screen.
- **Responsive Design:** Ensures compatibility across different devices with consistent visuals.
- **Pure CSS Magic:** No JavaScript required!

---

## 🌟 Live Demo

<iframe height="600" style="width: 100%;" scrolling="no" title="happy-new-year-animation" src="https://codepen.io/Sambit-Nanda/embed/mybRKvy?default-tab=html&theme-id=dark" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/Sambit-Nanda/pen/mybRKvy">
  happy-new-year-animation</a> by Sambit Nanda (<a href="https://codepen.io/Sambit-Nanda">@Sambit-Nanda</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

---

## 💻 Code Overview

### 1. **HTML Structure**

The HTML is simple and semantic, with a clear division of elements for the greeting, year, balloon, and fireworks.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy New Year</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="feliz">Happy New Year</div>
    <div class="ano_novo">
        <span>202</span>
        <span class="seis">4</span>
        <span class="sete">5</span>
        <div class="balao"></div>
    </div>
    <div class="fogos">
        <div class="f1"><span><i></i></span></div>
        <div class="f2"><span><i></i></span></div>
        <div class="f3"><span><i></i></span></div>
        <div class="f4"><span><i></i></span></div>
    </div>
    <a href="https://thefrontcoder.com" class="author">thefrontcoder.com</a>
</body>
</html>
```

---

### 2. **CSS for Styling and Animation**

The CSS handles everything, from styling the text to animating the balloon and fireworks. Here's the magic behind the scenes:

#### Styling the Background and Text
```css
html {
    background: #222048; /* Dark festive theme */
}

.feliz {
    font-family: 'Pacifico', cursive;
    font-size: 100px;
    color: #f48fb1;
    text-align: center;
    animation: vem_feliz 2s ease-in-out 7s forwards;
}
```

#### Animating the Year Transition
```css
.ano_novo > span {
    font-family: 'Montserrat', sans-serif;
    font-size: 175px;
    font-weight: bold;
    color: #7a8fe8;
}

span.sete {
    animation: vem_2017 6s ease-in-out forwards;
}

@keyframes vem_2017 {
    0% { right: 0%; }
    66.666% { right: 50%; margin-right: -300px; }
    100% { right: 50%; }
}
```

#### Adding the Balloon Animation
```css
.balao {
    width: 100px;
    height: 100px;
    background: #e8d57a;
    border-radius: 50%;
    animation: vem_e_vai_balao 10s ease-in-out forwards;
}

@keyframes vem_e_vai_balao {
    0% { top: 50%; right: 0%; }
    50% { top: -100%; right: 50%; }
    100% { top: -150%; right: 50%; }
}
```

#### Crafting the Fireworks
```css
.fogos > div {
    border: 2px solid #fff;
    animation: solta_fogos 1.5s ease-in-out 8s forwards;
}

@keyframes solta_fogos {
    0% { width: 2px; height: 30px; opacity: 0; }
    100% { width: 10px; height: 10px; opacity: 1; transform: scale(1); }
}
```

---

## 🎨 Customization

Feel free to tweak the colors, timing, and animations to fit your own style:
- **Colors:** Update the colors to match your theme.
- **Fonts:** Use your favorite Google Fonts for a unique look.
- **Fireworks Timing:** Adjust the animation delays for a synchronized display.

---

## 🔧 Tools Used
- **HTML5**
- **CSS3**
- **Google Fonts:** 'Pacifico' and 'Montserrat'

---

## 💡 Tips for Enhancing the Animation
1. **Sound Effects:** Add New Year sound effects using JavaScript for an interactive experience.
2. **Countdown Timer:** Incorporate a timer to count down to the New Year.
3. **Confetti Effect:** Add falling confetti for extra flair.

---

## 🚀 Get Inspired

If you enjoyed this animation, don't forget to check out more projects on [thefrontcoder.com](https://thefrontcoder.com) for frontend inspiration and tutorials.

---

🎉 **Happy New Year 2025!** Let's make it amazing with code and creativity!
