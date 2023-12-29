# Mini Drawing Project Readme
![image](https://github.com/KalpanaMamnani/CanvasProject/assets/37242267/45a344a8-46bc-407b-af89-608922f44dc9)


## Description
This JavaScript project is a mini drawing application that allows users to draw on an HTML canvas element. Users can customize the pen color and width, save their drawings as images, and clear the canvas when needed.

## Features
- **Drawing:** Users can draw on the canvas by clicking and dragging the mouse.
- **Customization:** The pen color and width can be customized using input elements.
- **Save Image:** Users can save their drawings as images with a customizable filename.
- **Clear Canvas:** There is an option to clear the entire canvas with a confirmation prompt.

## Usage
1. Open the HTML file in a web browser.
2. Use the color picker and input elements to customize the pen color and width.
3. Click and drag on the canvas to draw.
4. Click the "Save" button to save the drawing as an image.
5. Click the "Clear" button to clear the canvas (with a confirmation prompt).

## Code Overview

### Drawing Functionality

```javascript
// Function to draw on the canvas
function draw(val) {
     if (val === 'up') {
            m.draw = false;
        }
        if (val === 'down') {
            m.draw = true;
        }
        if (m.draw) {
            console.log('drawing');
            ctx.beginPath();
            ctx.moveTo(m.lastX, m.lastY);
            ctx.lineTo(m.x, m.y);
            ctx.strokeStyle = penColor.value;
            ctx.lineWidth = penWidth.value;
            ctx.stroke();
            ctx.closePath();
        }
}
```

- The `draw` function handles the drawing logic based on mouse events.
- It sets the drawing state (`m.draw`) based on mouse down and up events.
- The main drawing logic is encapsulated in the conditional block where a line is drawn between the last and current mouse coordinates.

### Save Image Functionality

```javascript
// Function to save the drawing as an image
function saveImg() {
        const dataURL = canvas.toDataURL();
        console.log(dataURL);
        const link = document.createElement('a');
        document.body.appendChild(link);
        link.setAttribute('download', 'image.png');
        link.href = dataURL;
        link.click();
        document.body.removeChild(link);
}
```

- The `saveImg` function converts the canvas content to a data URL.
- It creates a download link dynamically, sets the filename, and triggers a click to prompt the user to save the image.

### Clear Canvas Functionality

```javascript
// Function to clear the canvas with confirmation
function clearImg() {
        let temp = confirm('Clear confirm?');
        if (temp) {
            ctx.clearRect(0, 0, canvas.offsetWidth, canvas.offsetHeight);
        }
}
```

- The `clearImg` function displays a confirmation prompt and proceeds to clear the canvas if the user confirms.
- The main clearing logic uses `ctx.clearRect` to erase the entire canvas.

## Additional Notes
- The drawing coordinates are calculated based on mouse movements relative to the canvas.
- Users are prompted for confirmation before clearing the canvas to prevent accidental data loss.

Feel free to customize and expand upon this mini drawing project to suit your needs!
