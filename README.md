# Headroom.js (Modern ES6+ Optimized Fork)

A modern, optimized, and **ES6** rewritten version of the popular [headroom.js](https://github.com/WickyNilliams/headroom.js/), designed to hide or show your page's header based on scroll direction, improving mobile user experience and saving valuable screen real estate.

This variant brings major performance improvements, code cleanliness, and new native features, dropping legacy dependencies in favor of modern web standards.

---

## ✨ What's New Compared to the Original (`WickyNilliams/headroom.js`)?

*   **Modern ES6+ Syntax & Private Fields:** Fully rewritten using modern JavaScript classes, private fields (`#parsedClasses`, `#scrollerAdapter`, `#rafId`, `#resizeObserver`) for superior encapsulation, and the prevention of global scope pollution.
*   **Optimized Performance (RAF):** Scroll and resize state updates are natively synchronized using `requestAnimationFrame` (`requestAnimationFrame` / `cancelAnimationFrame`), preventing browser overload and ensuring a smooth 60fps framerate.
*   **`ResizeObserver` Integration:** Beyond listening to standard window `resize` events, it natively leverages `ResizeObserver` to automatically detect real-time dimension changes on the monitored element.
*   **Native Support for Custom Scrollable Elements:** In addition to window scrolling (`window`), the internal adapter efficiently handles individual scrollable containers (`overflow: auto/scroll`).
*   **Zero Dependencies:** No jQuery, no external libraries. Pure modern JavaScript, easily integrated into any framework or vanilla application.

---

## 🚀 Installation & Usage

### 1. Importing as an ES Module
```javascript
import Headroom from './headroom.js'; // or the correct path to your file

// Find the header element on the page
const myHeader = document.querySelector('header');

// Initialize with optional configuration
const headroom = new Headroom(myHeader, {
    offset: 205, // Trigger effect after 205px of scrolling
    tolerance: {
        up: 5,
        down: 0
    },
    classes: {
        initial: 'headroom',
        pinned: 'headroom--pinned',
        unpinned: 'headroom--unpinned',
        top: 'headroom--top',
        notTop: 'headroom--not-top'
    },
    onPin: function() { /* callback on pin */ },
    onUnpin: function() { /* callback on unpin */ },
    onTop: function() { /* callback when at the top */ },
    onNotTop: function() { /* callback when scrolled down */ }
});

// Start the event listeners
headroom.init();
```

---

## 🎨 CSS Classes Used

The component automatically adds and removes the following classes on the target element, allowing you to apply smooth CSS transitions (e.g., `transform: translateY(-100%)`):

*   `headroom` – Applied upon initialization.
*   `headroom--pinned` / `headroom--unpinned` – Depending on the scroll direction (visible / hidden).
*   `headroom--top` / `headroom--not-top` – Indicates whether the user is at the top of the page.
*   `headroom--bottom` / `headroom--not-bottom` – Indicates whether the bottom edge of the page has been reached.
*   `headroom--frozen` – When the state is programmatically frozen.

---

## 🛠️ API & Available Methods

*   `headroom.init()` – Activates event listeners and determines the initial state.
*   `headroom.destroy()` – Cleans up event listeners, observers, and added classes (stops execution).
*   `headroom.pin()` – Forces the header to show.
*   `headroom.unpin()` – Forces the header to hide.
*   `headroom.freeze()` – Freezes the current state (ignores scrolling).
*   `headroom.unfreeze()` – Unfreezes the state.

---

## 📄 License

This project is an optimized fork of [headroom.js](https://github.com/WickyNilliams/headroom.js/) and is distributed under the **MIT** license.
