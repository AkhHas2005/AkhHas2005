# Creating a Random Image Generator in JavaScript  

## Me
I want to make a random image generator in Javascript as a html webpage. The randomised images should be all be from a subfolder called "pics", there should be a next button that pulls up the next random image and a back button that goes to the previous image and a randomise button that changes the random order. How can I make this?  

## Co-Pilot
Great, let's get started with creating your random image generator! Here’s a basic outline of what we need to do:

1. Create an HTML structure with buttons and an image placeholder.
2. Write JavaScript code to handle the image randomization and navigation.
3. Store your images in a subfolder called "pics".

Here's a sample implementation to get you going:

### HTML Structure
Create an HTML file (e.g., `index.html`) with the following content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Image Generator</title>
    <style>
        #image-container img {
            width: 500px;
            height: auto;
        }
    </style>
</head>
<body>
    <div id="image-container">
        <img id="random-image" src="pics/image1.jpg" alt="Random Image">
    </div>
    <button onclick="showPreviousImage()">Back</button>
    <button onclick="showRandomImage()">Next</button>
    <button onclick="randomizeOrder()">Randomize</button>

    <script src="script.js"></script>
</body>
</html>
```

### JavaScript Logic
Create a JavaScript file (e.g., `script.js`) with the following content:

```javascript
// List of images in the "pics" folder
const images = ["pics/image1.jpg", "pics/image2.jpg", "pics/image3.jpg", "pics/image4.jpg"];
let currentIndex = 0;
let shuffledIndexes = shuffleArray([...Array(images.length).keys()]);

function showImage(index) {
    const imgElement = document.getElementById("random-image");
    imgElement.src = images[index];
}

function showPreviousImage() {
    currentIndex = (currentIndex - 1 + images.length) % images.length;
    showImage(shuffledIndexes[currentIndex]);
}

function showRandomImage() {
    currentIndex = (currentIndex + 1) % images.length;
    showImage(shuffledIndexes[currentIndex]);
}

function randomizeOrder() {
    shuffledIndexes = shuffleArray([...Array(images.length).keys()]);
    currentIndex = 0;
    showImage(shuffledIndexes[currentIndex]);
}

function shuffleArray(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
    }
    return array;
}

// Initialize with the first image
showImage(shuffledIndexes[currentIndex]);
```

### Folder Structure
Ensure your folder structure looks something like this:

```
project-folder/
│
├── index.html
├── script.js
└── pics/
    ├── image1.jpg
    ├── image2.jpg
    ├── image3.jpg
    └── image4.jpg
```

This should give you a functional random image generator! You can expand and modify the code according to your needs. Enjoy coding! 😃  

### References  

[1. github.com](https://github.com/buribalazs/smooth-drag-order/tree/7b40d21d076c3e31765f61481f537beaf4c5ec9f/README.md) 
[2. github.com](https://github.com/Vidito/quotes/tree/c09bb974bab33aaf0506dd8fb26f46873486329c/index.php) 
[3. github.com](https://github.com/lineupninja/clearchat/tree/a40a41b8161aaafb72040349afce3d9138e396e7/brochure%2Fapp%2Fcomponents%2Fpage%2Findex%2Fservices.ts) 
[4. github.com](https://github.com/derycklong/PluralSight-Angular-Tutorial/tree/f841c806af1dc94e9316799fbcee7b3cc1a0c086/node_modules%2Fsocks%2Fbuild%2Fcommon%2Futil.js)  

## Me
Almost there, however, I want the images list to dynamically adapt to all image sin the pics folder e.g. if there are 10 images, all 10 image names should be in there, if 5 images are added before running again, these 5 images should now be included in the images list. Can you do that?  

## Co-Pilot
Absolutely! To achieve this, you can use the Fetch API to dynamically load the image file names from the server. You would need a server-side script (e.g., using Node.js) to read the contents of the "pics" folder and return the list of images. 

Here’s a basic example using Node.js:

### Node.js Server Script
First, create a new file (e.g., `server.js`) in your project folder with the following content:

```javascript
const express = require('express');
const fs = require('fs');
const path = require('path');
const app = express();
const port = 3000;

// Serve static files from the project folder
app.use(express.static(__dirname));

app.get('/images', (req, res) => {
    const picsDir = path.join(__dirname, 'pics');
    fs.readdir(picsDir, (err, files) => {
        if (err) {
            return res.status(500).send('Unable to scan directory');
        }
        const imageFiles = files.filter(file => /\.(jpg|jpeg|png|gif)$/i.test(file));
        res.json(imageFiles);
    });
});

app.listen(port, () => {
    console.log(`Server is running at http://localhost:${port}`);
});
```

### HTML and JavaScript
Update your `index.html` and `script.js` to fetch the images dynamically:

#### `index.html`
Make sure your script tag is updated to include the JavaScript code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Image Generator</title>
    <style>
        #image-container img {
            width: 500px;
            height: auto;
        }
    </style>
</head>
<body>
    <div id="image-container">
        <img id="random-image" src="" alt="Random Image">
    </div>
    <button onclick="showPreviousImage()">Back</button>
    <button onclick="showRandomImage()">Next</button>
    <button onclick="randomizeOrder()">Randomize</button>

    <script src="script.js"></script>
</body>
</html>
```

#### `script.js`
Update your script to fetch the images from the server:

```javascript
let images = [];
let currentIndex = 0;
let shuffledIndexes = [];

function fetchImages() {
    fetch('/images')
        .then(response => response.json())
        .then(data => {
            images = data.map(file => `pics/${file}`);
            shuffledIndexes = shuffleArray([...Array(images.length).keys()]);
            showImage(shuffledIndexes[currentIndex]);
        })
        .catch(error => console.error('Error fetching images:', error));
}

function showImage(index) {
    const imgElement = document.getElementById("random-image");
    imgElement.src = images[index];
}

function showPreviousImage() {
    currentIndex = (currentIndex - 1 + images.length) % images.length;
    showImage(shuffledIndexes[currentIndex]);
}

function showRandomImage() {
    currentIndex = (currentIndex + 1) % images.length;
    showImage(shuffledIndexes[currentIndex]);
}

function randomizeOrder() {
    shuffledIndexes = shuffleArray([...Array(images.length).keys()]);
    currentIndex = 0;
    showImage(shuffledIndexes[currentIndex]);
}

function shuffleArray(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
    }
    return array;
}

// Initialize by fetching images from the server
fetchImages();
```

### Folder Structure
Ensure your folder structure now looks something like this:

```
project-folder/
│
├── index.html
├── script.js
├── server.js
└── pics/
    ├── image1.jpg
    ├── image2.jpg
    ├── image3.jpg
    └── (other images...)
```

### Running the Server
Make sure you have Node.js and npm installed. Then, in your project directory, run:

```sh
npm init -y
npm install express
node server.js
```

This should start your server on `http://localhost:3000` and dynamically fetch images from the "pics" folder.

Give it a try and let me know how it goes! 😃  

### References  

[1. github.com](https://github.com/Vidito/quotes/tree/c09bb974bab33aaf0506dd8fb26f46873486329c/index.php) 
[2. github.com](https://github.com/lineupninja/clearchat/tree/a40a41b8161aaafb72040349afce3d9138e396e7/brochure%2Fapp%2Fcomponents%2Fpage%2Findex%2Fservices.ts) 
[3. github.com](https://github.com/derycklong/PluralSight-Angular-Tutorial/tree/f841c806af1dc94e9316799fbcee7b3cc1a0c086/node_modules%2Fsocks%2Fbuild%2Fcommon%2Futil.js)  

## Me
Assume I can't use Node.js or any external server, I'm hosting the repo using GitHub pages  

## Co-Pilot
Got it! Since we can't use server-side scripting, we'll have to use a different approach to dynamically manage the list of images. One way to achieve this is to manually maintain a JSON file that lists all the images. Every time you add new images to the "pics" folder, you'll need to update this JSON file.

Here’s how you can do it:

### Folder Structure
Ensure your folder structure looks something like this:

```
project-folder/
│
├── index.html
├── script.js
├── images.json
└── pics/
    ├── image1.jpg
    ├── image2.jpg
    ├── image3.jpg
    └── (other images...)
```

### JSON File
Create a JSON file (e.g., `images.json`) that lists all the images in the "pics" folder:

```json
[
    "pics/image1.jpg",
    "pics/image2.jpg",
    "pics/image3.jpg"
]
```

### HTML and JavaScript
Update your `index.html` and `script.js` to load the images from the JSON file.

#### `index.html`
Ensure your script tag is updated to include the JavaScript code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Image Generator</title>
    <style>
        #image-container img {
            width: 500px;
            height: auto;
        }
    </style>
</head>
<body>
    <div id="image-container">
        <img id="random-image" src="" alt="Random Image">
    </div>
    <button onclick="showPreviousImage()">Back</button>
    <button onclick="showRandomImage()">Next</button>
    <button onclick="randomizeOrder()">Randomize</button>

    <script src="script.js"></script>
</body>
</html>
```

#### `script.js`
Update your script to fetch the images from the JSON file:

```javascript
let images = [];
let currentIndex = 0;
let shuffledIndexes = [];

function fetchImages() {
    fetch('images.json')
        .then(response => response.json())
        .then(data => {
            images = data;
            shuffledIndexes = shuffleArray([...Array(images.length).keys()]);
            showImage(shuffledIndexes[currentIndex]);
        })
        .catch(error => console.error('Error fetching images:', error));
}

function showImage(index) {
    const imgElement = document.getElementById("random-image");
    imgElement.src = images[index];
}

function showPreviousImage() {
    currentIndex = (currentIndex - 1 + images.length) % images.length;
    showImage(shuffledIndexes[currentIndex]);
}

function showRandomImage() {
    currentIndex = (currentIndex + 1) % images.length;
    showImage(shuffledIndexes[currentIndex]);
}

function randomizeOrder() {
    shuffledIndexes = shuffleArray([...Array(images.length).keys()]);
    currentIndex = 0;
    showImage(shuffledIndexes[currentIndex]);
}

function shuffleArray(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
    }
    return array;
}

// Initialize by fetching images from the JSON file
fetchImages();
```

### Updating Images
Whenever you add new images to the "pics" folder, make sure to update `images.json` with the new image paths. This way, your image list will dynamically adapt without needing server-side scripting.

Give this a try and let me know how it works for you! 😃  

### References  

[1. github.com](https://github.com/Vidito/quotes/tree/c09bb974bab33aaf0506dd8fb26f46873486329c/index.php) 
[2. github.com](https://github.com/lineupninja/clearchat/tree/a40a41b8161aaafb72040349afce3d9138e396e7/brochure%2Fapp%2Fcomponents%2Fpage%2Findex%2Fservices.ts) 
[3. github.com](https://github.com/derycklong/PluralSight-Angular-Tutorial/tree/f841c806af1dc94e9316799fbcee7b3cc1a0c086/node_modules%2Fsocks%2Fbuild%2Fcommon%2Futil.js)  

*End of this Conversation*
