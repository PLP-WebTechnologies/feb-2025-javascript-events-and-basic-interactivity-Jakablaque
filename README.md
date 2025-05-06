# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!



### 1. `index.html`: The Playground

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive JavaScript Event Assignment</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <!-- Button for text and color change -->
  <button id="actionBtn">Click Me!</button>

  <!-- Image Gallery -->
  <div id="gallery">
    <img src="image1.jpg" alt="Image 1">
    <img src="image2.jpg" alt="Image 2">
    <img src="image3.jpg" alt="Image 3">
  </div>

  <!-- Tabs for content display -->
  <div class="tabs">
    <button class="tablink" onclick="openTab(event, 'tab1')">Tab 1</button>
    <button class="tablink" onclick="openTab(event, 'tab2')">Tab 2</button>
  </div>

  <div id="tab1" class="tabcontent">
    <h3>Tab 1</h3>
    <p>Some content for Tab 1.</p>
  </div>

  <div id="tab2" class="tabcontent">
    <h3>Tab 2</h3>
    <p>Some content for Tab 2.</p>
  </div>

  <!-- Form for validation -->
  <form id="form" action="#">
    <label for="email">Email:</label>
    <input type="email" id="email" required><br>

    <label for="password">Password:</label>
    <input type="password" id="password" minlength="8" required><br>

    <button type="submit">Submit</button>
  </form>

  <script src="script.js"></script>
</body>
</html>
```

---

2. `style.css

```css
/* Basic styles for the page */
body {
  font-family: Arial, sans-serif;
  padding: 20px;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background-color: lightblue;
}

#gallery img {
  width: 100px;
  height: 100px;
  margin: 5px;
  cursor: pointer;
}

.tabs {
  display: flex;
}

.tablink {
  padding: 10px 20px;
  cursor: pointer;
  margin: 5px;
}

.tabcontent {
  display: none;
  margin-top: 20px;
}

/* Show active tab content */
.tabcontent.active {
  display: block;
}
```

---

##3. `script.js`: JavaScript Wizardry

```javascript
// Event Handling: Button Click & Hover
const actionBtn = document.getElementById('actionBtn');

// Button click: Change text and color
actionBtn.addEventListener('click', function() {
  this.textContent = 'You clicked me!';
  this.style.backgroundColor = 'green';
});

// Button hover: Change style on hover
actionBtn.addEventListener('mouseover', function() {
  this.style.backgroundColor = 'blue';
});

actionBtn.addEventListener('mouseout', function() {
  this.style.backgroundColor = 'gray';
});

// Keypress detection: Detect any key press and log it
document.addEventListener('keypress', function(event) {
  console.log('Key pressed: ' + event.key);
});

// Double-click or long press to perform a secret action
actionBtn.addEventListener('dblclick', function() {
  alert('Double-click detected!');
});

// Gallery: Show image on click
const images = document.querySelectorAll('#gallery img');
images.forEach(image => {
  image.addEventListener('click', function() {
    alert('Image clicked: ' + this.alt);
  });
});

// Tabs: Show content when clicked
function openTab(event, tabName) {
  const tabContents = document.querySelectorAll('.tabcontent');
  tabContents.forEach(tab => {
    tab.classList.remove('active');
  });

  const activeTab = document.getElementById(tabName);
  activeTab.classList.add('active');
}

// Form Validation
const form = document.getElementById('form');
form.addEventListener('submit', function(event) {
  const email = document.getElementById('email').value;
  const password = document.getElementById('password').value;

  // Simple email and password validation
  const emailPattern = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;

  if (!email.match(emailPattern)) {
    alert('Please enter a valid email address.');
    event.preventDefault();
  } else if (password.length < 8) {
    alert('Password must be at least 8 characters.');
    event.preventDefault();
  } else {
    alert('Form submitted successfully!');
  }
}
