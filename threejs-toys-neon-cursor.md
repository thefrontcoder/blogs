
# ThreeJS Toys - Neon Cursor

In this tutorial, we’ll explore how to create a glowing, interactive **neon cursor** using **ThreeJS**. The cursor will be a 3D object that responds to user movements, creating a unique and eye-catching effect for web projects. This is a fun and engaging way to bring your website to life by adding an interactive element that goes beyond the usual static mouse pointer.

## What You'll Learn

- How to use **ThreeJS** and **WebGL** to create a 3D cursor.
- Adding glowing effects using shaders and lighting techniques.
- Making the cursor interactive, so it reacts to user movements and page elements.
- Using CSS and JavaScript to enhance user experience with smooth animations and transitions.

## Why ThreeJS?

[ThreeJS](https://threejs.org/) is a powerful JavaScript library that makes working with WebGL easier. It allows developers to create 3D graphics that are rendered in the browser, making it ideal for interactive animations, games, and visualizations. In this tutorial, we'll use ThreeJS to create a custom cursor that reacts to mouse movements and incorporates neon glow effects.

## Live Demo

To get a better understanding of how the neon cursor looks and behaves, check out this live demo of the ThreeJS-powered cursor:

<iframe height="600" style="width: 100%;" scrolling="no" title="ThreeJS Toys - Neon Cursor" src="https://codepen.io/soju22/embed/wvyBorP?default-tab=html&theme-id=dark" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/soju22/pen/wvyBorP">ThreeJS Toys - Neon Cursor</a> by Kevin Levron (<a href="https://codepen.io/soju22">@soju22</a>) on <a href="https://codepen.io">CodePen</a>.
</iframe>

## Steps to Create the Neon Cursor

### 1. Set Up Your Environment

Start by setting up a basic HTML file that includes the ThreeJS library. You can either download it from the [ThreeJS website](https://threejs.org/) or link to a CDN version in your HTML:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
```

### 2. Create the 3D Scene

Next, you need to create a 3D scene with ThreeJS. This includes setting up a camera, a renderer, and a light source. The scene will serve as the canvas for your neon cursor.

```javascript
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);
```

### 3. Add the Neon Cursor

The neon effect can be achieved by adding a glowing sphere or another 3D object that follows the mouse pointer. Here's an example of how you can create a glowing cursor:

```javascript
const geometry = new THREE.SphereGeometry(1, 32, 32);
const material = new THREE.MeshBasicMaterial({
  color: 0x00ff00, // Neon green
  emissive: 0x00ff00, // Glowing effect
  emissiveIntensity: 0.5
});
const cursor = new THREE.Mesh(geometry, material);
scene.add(cursor);
```

### 4. Update Cursor Position

Use JavaScript to update the cursor's position based on mouse movement:

```javascript
document.addEventListener('mousemove', (event) => {
  const mouseX = (event.clientX / window.innerWidth) * 2 - 1;
  const mouseY = -(event.clientY / window.innerHeight) * 2 + 1;

  cursor.position.x = mouseX * 5;
  cursor.position.y = mouseY * 5;
});
```

### 5. Add Animation and Lighting

To enhance the effect, you can add animations and lighting. The glowing neon effect becomes more prominent when you animate the scene.

```javascript
const animate = function () {
  requestAnimationFrame(animate);

  renderer.render(scene, camera);
};

animate();
```

### 6. Styling and Finishing Touches

To complete the look, add some CSS to hide the default cursor and allow the custom 3D cursor to take over.

```css
body {
  margin: 0;
  overflow: hidden;
}

canvas {
  display: block;
}

* {
  cursor: none;
}
```

## Conclusion

In this tutorial, we’ve created a custom **neon cursor** using **ThreeJS**. You can experiment with different effects, shapes, and animations to make your cursor more interactive and dynamic. This project is a fun way to explore 3D graphics and WebGL, and it adds a creative touch to your web projects.

Feel free to explore the live demo and experiment with the code to create your own glowing cursor effect!

---

If you're interested in learning more about **ThreeJS** and other fun 3D web projects, check out the official documentation or explore additional tutorials on building interactive web experiences with ThreeJS.

Happy coding! 🚀
