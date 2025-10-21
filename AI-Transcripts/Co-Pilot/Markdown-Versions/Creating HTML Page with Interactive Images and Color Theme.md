# Creating HTML Page with Interactive Images and Color Theme  

## Me
How can I create a html page with a sky blue and gray theme colours with cream and dark yellow as secondary colours to display 3 images in a row atht pop out when you hover over them and when you click, links to a different web page?  

## Co-Pilot
[1]: https://github.com/apple54whn/notes/tree/1c343bed00a22b25f25465f19000a728362c1939/docs%2FFront%20End%2FVue%2F2-1%20%E6%8F%92%E5%80%BC%E8%AF%AD%E6%B3%95.md ""

Absolutely, Hasan! Here's a step-by-step guide to creating that HTML page with your color palette and interactive image features:

---

### 🌈 Theme Setup
We'll use:
- **Primary colors**: Sky blue (`#87CEEB`) and gray (`#808080`)
- **Secondary colors**: Cream (`#FFFDD0`) and dark yellow (`#FFD700`)

---

### 🖼️ Image Display Requirements
- Display 3 images **side by side**
- On **hover**, each image slightly "pops out" (scales up)
- On **click**, each links to a different webpage

---

### 💻 Code Implementation

#### 1. **HTML Structure**
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Image Showcase</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <div class="container">
    <div class="image-box">
      <a href="https://example1.com">
        <img src="image1.jpg" alt="Image 1" />
      </a>
    </div>
    <div class="image-box">
      <a href="https://example2.com">
        <img src="image2.jpg" alt="Image 2" />
      </a>
    </div>
    <div class="image-box">
      <a href="https://example3.com">
        <img src="image3.jpg" alt="Image 3" />
      </a>
    </div>
  </div>
</body>
</html>
```

#### 2. **CSS Styling (styles.css)**
```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #87CEEB; /* sky blue */
  color: #808080; /* gray */
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 50px;
  background-color: #FFFDD0; /* cream */
}

.image-box {
  margin: 0 15px;
  transition: transform 0.3s ease;
}

.image-box img {
  width: 250px;
  border: 5px solid #FFD700; /* dark yellow */
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(128, 128, 128, 0.5); /* gray shadow */
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.image-box:hover img {
  transform: scale(1.1);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.4);
}
```

---

### ✅ Notes
- Make sure your image paths (`image1.jpg`, etc.) are correct.
- You can swap out the link URLs with ones that fit your needs.
- Want the colors to animate or shift subtly when hovered? I can help with that too!

Would you like to make the layout responsive for mobile devices or add titles/captions to each image?  

### References
[github.com](https://github.com/apple54whn/notes/tree/1c343bed00a22b25f25465f19000a728362c1939/docs%2FFront%20End%2FVue%2F2-1%20%E6%8F%92%E5%80%BC%E8%AF%AD%E6%B3%95.md)    

*End of this Conversation*
