---
title: "TEAC 105 Week 1 Solution"
description: "What was done in Week 1"
publishDate: "28 Nov 2025"
tags: ["teac105", "week 1"]
pinned: true
---

```js
/*

Jason Cumiskey

TEAC 105 Week 1

Rock-Paper-Scissors Rules

1. Christmas Tree crush the Scissors
2. Scissors cuts the Bacon
3. Bacon wraps Christmas Tree
*/



let x = 25;
let y = 200;

let diameter = 50;
let sf = diameter / 100;

// Size of the Emojis
let size = 20;
// Speed and Direction for x
let speedX = [];
let directionX = [];

// Speed and Direction for y
let speedY = [];
let directionY = [];

function setup() {
  createCanvas(400, 400);

  directionX.push(random([-1,1]));
  directionY.push(random([-1,1]));

  speedX.push(random(5));
  speedY.push(random(5));
}

function draw() {
  background(220);

  smileyFaceMaker(x, y);
  //smileyFaceMaker(x + 50, y);
  //smileyFaceMaker(50, 200);
  // draw an emoji
  drawEmoji("🎄", 100, 100);
  drawEmoji("✂️", 50, 50);
  drawEmoji("🥓", 30, 30);

  edgeDetect();
  setSpeed();
  //print(frameRate());

}

function smileyFaceMaker(x, y) {
  /*
     Im drawing a
     circle here!
  */
  fill("yellow");
  circle(x, y, diameter);
  // draw some eyes
  fill("black");
  circle(x - 20 * sf, y - 20 * sf, 20 * sf);
  circle(x + 20 * sf, y - 20 * sf, 20 * sf);
  arc(x + 0 * sf, y + 10 * sf, 60 * sf, 50 * sf, 0, PI, CHORD);
}

function drawEmoji(emoji, x, y) {
  textSize(size);
  text(emoji, x, y);
}

function edgeDetect(i) {
  // Edge Detect Horizontal
  if ( x + diameter/2 >= width ) directionX[i] = -1;
  else if ( x - diameter/2 <= 0 ) directionX[i] = 1;

  // Edge Detect Vertical (y)
  if ( y + diameter/2 >= height ) directionY[i] = -1;
  else if ( y - diameter/2 <= 0 ) directionY[i] = 1;
}

function setSpeed(i) {
  // Set Horizontal Speed
  if ( directionX[i] === 1 ) x += speedX[i];
  else if ( directionX[i] === -1 ) x-= speedX[i];

  // Set Vertical (y) Speed
  if ( directionY[i] === 1 ) y += speedY[i];
  else if ( directionY[i] === -1 ) y-= speedY[i];
}
```
