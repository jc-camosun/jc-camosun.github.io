---
title: "TEAC 105 Assignment 2 Solution"
description: "This is the solution to Assignment 2!"
publishDate: "18 Nov 2025"
tags: ["teac105", "assignment 2"]
pinned: true
---

```js
/*********************************
 *
 * TEAC 105 Explorations in Tech
 *
 * Week 2 Sample Solution
 *
 * Jason Cumiskey
 *
 * Rock-Paper-Scissors Simulation
 *
 * RULES:
 * 1. Jack-O-Lantern crushes Scissors
 * 2. Scissors cuts Pizza
 * 3. Pizza wraps Jack-O-Lantern
 *
 **********************************/

// x and y for Smiley Faces
//let x = [ 10, 200 ];
//let y = [ 200, 10 ];

// xand y for the Emojis!
let x = [-4, 180, 377];
let y = [397, 22, 399];
let size = 25;
let diameter = 20;
let directionX = [];
let directionY = [];
let speedX = [];
let speedY = [];
let speed = 5;

function setup() {
  // The canvas is 400 pixels across
  // by 400 pixels down
  createCanvas(400, 400);

  // Assignment #2
  // Jack-O-Lantern Emoji
  directionX.push(random([-1, 1]));
  directionY.push(random([-1, 1]));
  speedX.push(random(speed));
  speedY.push(random(speed));

  // Pizza Emoji
  directionX.push(random([-1, 1]));
  directionY.push(random([-1, 1]));
  speedX.push(random(speed));
  speedY.push(random(speed));

  // Scissors Emoji
  directionX.push(random([-1, 1]));
  directionY.push(random([-1, 1]));
  speedX.push(random(speed));
  speedY.push(random(speed));

  // debug and info
  // print(directionX);
  // print(directionY);
  // print(speedX);
  // print(speedY);
}

// detect horizontal and vertical edges
function edgeDetect(i) {
  // horizontal edge detection
  if (x[i] + diameter / 2 >= width) {
    directionX[i] = -1;
  } else if (x[i] - diameter / 2 <= 0) {
    directionX[i] = 1;
  }

  // vertical edge detection
  if (y[i] + diameter / 2 >= height) {
    directionY[i] = -1;
  } else if (y[i] - diameter / 2 <= 0) {
    directionY[i] = 1;
  }
}

// detect horizontal and vertical edges
// for Emojis!
function edgeDetectEmoji(i) {
  // horizontal edge detection
  if (x[i] + size > width) {
    directionX[i] = -1;
  } else if (x[i] < 0) {
    directionX[i] = 1;
  }

  // vertical edge detection
  if (y[i] > height) {
    directionY[i] = -1;
  } else if (y[i] - size < 0) {
    directionY[i] = 1;
  }
}

// set the horizontal and vertical speeds
function setSpeed(i) {
  // set horizontal speed
  if (directionX[i] === 1) {
    x[i] += speedX[i];
  } else if (directionX[i] === -1) {
    x[i] -= speedX[i];
  }

  // set vertical speed
  if (directionY[i] === 1) {
    y[i] += speedY[i];
  } else if (directionY[i] === -1) {
    y[i] -= speedY[i];
  }
}

function draw() {
  background(220);

  //print(frameRate())

  // Assignment #2
  // Jack-O-Lantern
  setSpeed(0);
  edgeDetectEmoji(0);

  // Pizza
  setSpeed(1);
  edgeDetectEmoji(1);

  // Scissors
  setSpeed(2);
  edgeDetectEmoji(2);

  // Assignment #2
  drawEmoji("🎃", x[0], y[0]);
  drawEmoji("🍕", x[1], y[1]);
  drawEmoji("✂", x[2], y[2]);
}

// Draws Emoji on Canvas
function drawEmoji(emoji, x, y) {
  textSize(size);
  text(emoji, x, y);
}
```
