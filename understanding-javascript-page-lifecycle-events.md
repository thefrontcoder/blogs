# Understanding JavaScript Page Lifecycle Events

JavaScript offers various events that help developers manage and interact with the different stages of an HTML page’s lifecycle. Understanding these events allows for smoother page behavior, especially when working with dynamically loaded content. This article covers the primary events you need to know: `DOMContentLoaded`, `load`, `beforeunload`, and `unload`, along with some related concepts.

## Key Page Lifecycle Events

The lifecycle of an HTML page involves several important events:

1. **DOMContentLoaded** – Triggered when the HTML has fully loaded and the DOM tree is built. External resources like images and stylesheets may still be loading.
2. **load** – Triggered when the entire page and all its resources (images, styles, etc.) are fully loaded.
3. **beforeunload/unload** – These events fire when the user is leaving the page. They’re useful for actions like checking if the user saved changes.

Each of these events has specific use cases:

- **DOMContentLoaded** – Allows scripts to interact with the DOM and initialize the UI.
- **load** – Executes once all resources are fully loaded, useful for cases where you need images or styles in place.
- **beforeunload/unload** – Executes as the user leaves, giving a chance to remind them to save changes.

Let's go deeper into these events and understand their specifics.

---

## The DOMContentLoaded Event

The `DOMContentLoaded` event fires when the HTML is completely loaded and parsed, though images and styles may still be loading.

### Usage Example

To catch this event, you need to use `addEventListener`:

```javascript
document.addEventListener("DOMContentLoaded", () => {
  console.log("DOM is ready!");
});
```

This event is perfect for running code that depends on the DOM but not on external resources, like images or stylesheets.

For example:

```html
<script>
  function initialize() {
    alert("DOM is ready!");
    // Image may not be fully loaded yet, so size could be 0x0
    alert(`Image size: ${img.offsetWidth}x${img.offsetHeight}`);
  }
  document.addEventListener("DOMContentLoaded", initialize);
</script>
<img id="img" src="image.png">
```

In this example, the `DOMContentLoaded` handler runs when the document’s DOM is ready, but the images or styles may not be fully loaded.

### How Scripts Affect DOMContentLoaded

JavaScript scripts inside the HTML block DOM construction until they finish executing. If a script has the `src` attribute, the browser waits for it to load before continuing. This ensures `DOMContentLoaded` waits for all scripts to be ready.

However, scripts with the `async` or `defer` attributes are exceptions:

- **async** – The browser continues processing the page while the script loads and executes as soon as it’s ready. Useful for independent scripts.
- **defer** – The browser continues processing, but defers the script’s execution until the document is fully parsed, right before `DOMContentLoaded`.

---

## The `load` Event

The `load` event triggers when the entire page, including all external resources like images and styles, is fully loaded. It’s useful when you need everything to be fully present on the page.

```javascript
window.onload = function() {
  console.log("Page fully loaded!");
};
```

In this example, `onload` ensures all images, stylesheets, and other resources are loaded, making it safe to retrieve image sizes and layout dimensions.

### Example with Image Size

```html
<script>
  window.onload = function() {
    console.log("Page loaded!");
    console.log(`Image size: ${img.offsetWidth}x${img.offsetHeight}`);
  };
</script>
<img id="img" src="image.png">
```

By using `window.onload`, you can be confident the image is fully loaded, and its dimensions are accessible.

---

## The `beforeunload` and `unload` Events

When users navigate away from the page, `beforeunload` and `unload` come into play. These events allow you to prompt users or take last-minute actions.

### `beforeunload`

The `beforeunload` event lets you prompt the user before they leave, such as checking for unsaved changes.

```javascript
window.onbeforeunload = function() {
  return "You have unsaved changes. Do you really want to leave?";
};
```

This event is useful to display a confirmation dialog, preventing accidental navigation away from the page.

> **Note:** Some browsers display a generic message instead of custom text for security reasons.

### `unload`

The `unload` event is similar but doesn’t allow any delays or prompts. It’s useful for cleanup tasks.

```javascript
window.onunload = function() {
  console.log("User has left the page");
};
```

The `unload` event is limited in functionality, but it can be handy for closing any open connections or sending final analytics data.

---

## `document.readyState`

If you’re uncertain about the document’s current state, `document.readyState` provides a reliable way to check it. This property has three states:

1. **loading** – The document is still loading.
2. **interactive** – The document is parsed but not fully loaded.
3. **complete** – The entire page, including resources, is fully loaded.

```javascript
if (document.readyState === "loading") {
  document.addEventListener("DOMContentLoaded", initialize);
} else {
  initialize();
}
```

This pattern ensures your code runs as soon as the DOM is ready, whether or not the script was loaded after `DOMContentLoaded`.

### Using `readystatechange` Event

The `readystatechange` event listens for changes in `document.readyState`, providing more granular control:

```javascript
document.addEventListener("readystatechange", () => {
  console.log("Current readyState:", document.readyState);
});
```

This method is less common but can be useful in certain cases.

---

## Event Timing Summary

Here's a quick summary of the page lifecycle timing:

1. **initial readyState: loading** – `document` starts loading.
2. **readyState: interactive** – The document is parsed.
3. **DOMContentLoaded** – The DOM is ready; external resources may still load.
4. **readyState: complete** – The document and all resources are fully loaded.
5. **window.onload** – The page is entirely loaded, safe for any further actions.

## Conclusion

JavaScript’s page lifecycle events give developers fine control over the loading and unloading stages. Here’s a quick recap:

- **DOMContentLoaded** – Triggers when the DOM is ready, ideal for setting up your interface.
- **load** – Fires when the full page, including resources, is loaded.
- **beforeunload/unload** – Executes when a user leaves the page, useful for confirming unsaved changes or performing quick cleanup tasks.
- **document.readyState** – Lets you track the document’s loading status, allowing for conditional execution.

Mastering these events ensures your web applications perform optimally, delivering a better user experience.
