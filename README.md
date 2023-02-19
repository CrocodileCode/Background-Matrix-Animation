# Background-Matrix-Animation
Matrix animations in JavaScript involve manipulating the content of a matrix to create an animation effect. One way to achieve this is by using the HTML canvas element, which provides a drawing surface that can be used to render graphics and animations in a web page. 

Here is a basic example of a matrix animation using JavaScript and the HTML canvas:

HTML :

<canvas id="canvas" width="500" height="500"></canvas>

JS:

var canvas = document.getElementById('canvas');
var ctx = canvas.getContext('2d');

var matrix = [
  ['0', '1', '0', '1'],
  ['1', '0', '1', '0'],
  ['0', '1', '0', '1'],
  ['1', '0', '1', '0']
];

var frameCount = 0;
var maxFrames = 50;

function animate() {
  frameCount++;
  if (frameCount >= maxFrames) {
    frameCount = 0;
    // rotate the matrix
    matrix.push(matrix.shift());
    for (var i = 0; i < matrix.length; i++) {
      matrix[i].push(matrix[i].shift());
    }
  }

  // clear the canvas
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // draw the matrix
  var cellSize = 20;
  var x = (canvas.width - cellSize * matrix[0].length) / 2;
  var y = (canvas.height - cellSize * matrix.length) / 2;
  for (var i = 0; i < matrix.length; i++) {
    for (var j = 0; j < matrix[i].length; j++) {
      if (matrix[i][j] == '1') {
        ctx.fillRect(x + j * cellSize, y + i * cellSize, cellSize, cellSize);
      }
    }
  }

  // request the next frame
  requestAnimationFrame(animate);
}

// start the animation
animate();


In this example, a matrix is defined as an array of arrays of characters ('0' or '1') that represents a pattern to be drawn on the canvas. The animate function is called repeatedly using requestAnimationFrame, and on each frame the matrix is rotated and redrawn on the canvas. The rotation is achieved by shifting the first row to the end and shifting each column to the right.

The canvas is cleared on each frame using the clearRect method, and the matrix is drawn using the fillRect method. The cellSize variable controls the size of each cell in the matrix, and the x and y variables determine the position of the matrix on the canvas. The frameCount variable is used to control the speed of the animation by limiting the number of frames between each rotation of the matrix.

This is just a basic example, and there are many ways to create more complex and interesting matrix animations using JavaScript and other web technologies.

# Project Preview :
![image](https://user-images.githubusercontent.com/121975087/219956993-090ea9cf-6d32-4bc4-9e8d-0e4da8a48033.png)

