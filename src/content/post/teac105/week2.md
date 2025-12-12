---
title: "TEAC 105 Week 2 Solution"
description: "This is the what we did in Week 2solution to Assignment 2!"
publishDate: "20 Nov 2025"
tags: ["teac105", "assignment 2"]
pinned: true
---

```js
/*

Jason Cumiskey

TEAC 105 Week 2

Rock-Paper-Scissors Rules

1. Christmas Tree crush the Scissors
2. Scissors cuts the Bacon
3. Bacon wraps Christmas Tree
*/

// Smiley Faces ;)
//let x = [25, 200];
//let y = [200, 25];

// Emojis
let x = [-4, 180, 377];
let y = [397, 22, 399];

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

let emoji = [];

let totalEmojis = 3;

// Type of Emojis
const CHRISTMASTREE = 0;
const SCISSORS = 1;
const BACON = 2;

function setup() {
  createCanvas(400, 400);

  // Emoji #1
  directionX.push(random([-1, 1]));
  directionY.push(random([-1, 1]));
  speedX.push(random(3));
  speedY.push(random(3));

  // Emoji #2
  directionX.push(random([-1, 1]));
  directionY.push(random([-1, 1]));
  speedX.push(random(3));
  speedY.push(random(3));

  // Emoji #3
  directionX.push(random([-1, 1]));
  directionY.push(random([-1, 1]));
  speedX.push(random(3));
  speedY.push(random(3));

  // Push the Emoji Types
  emoji.push(CHRISTMASTREE);
  emoji.push(SCISSORS);
  emoji.push(BACON);
}

function draw() {
  background(220);

  //smileyFaceMaker(x[0], y[0]);
  //smileyFaceMaker(x[1], y[1]);

  // draw an emoji

  for (let i = 0; i < totalEmojis; i += 1) {
    if (emoji[i] === CHRISTMASTREE) {
      drawEmoji("🎄", x[i], y[i]);
    } else if (emoji[i] === SCISSORS) {
      drawEmoji("✂️", x[i], y[i]);
    } else if (emoji[i] === BACON) {
      drawEmoji("🥓", x[i], y[i]);
    }
  }

  // Emoji #1
  edgeDetectEmoji(0);
  setSpeed(0);

  // Emoji #2
  edgeDetectEmoji(1);
  setSpeed(1);

  // Emoji #3
  edgeDetectEmoji(2);
  setSpeed(2);

  if (isColliding(0, 1)) {
    print("Christmas tree and the Scissors collided!!!");
  } else if (isColliding(0, 2)) {
    print("Christmas tree and the Bacon collided!!!");
  } else if (isColliding(1, 2)) {
    print("Scissors and Bacon collided!!!");
  }

  // Double for loop for Emojis to fight it out
  // if they have collided!!!
  for (let i = 0; i < totalEmojis; i += 1) {
    for (let j = i + 1; j < totalEmojis; j += 1) {
      if (isColliding(i, j)) {
        emoji[i] = fightItOut(i, j);
        emoji[j] = fightItOut(i, j);
      }
    }
  }
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
  if (x[i] + diameter / 2 >= width) directionX[i] = -1;
  else if (x[i] - diameter / 2 <= 0) directionX[i] = 1;

  // Edge Detect Vertical (y)
  if (y[i] + diameter / 2 >= height) directionY[i] = -1;
  else if (y[i] - diameter / 2 <= 0) directionY[i] = 1;
}

function edgeDetectEmoji(i) {
  // Edge Detect Horizontal
  if (x[i] + size > width) directionX[i] = -1;
  else if (x[i] < 0) directionX[i] = 1;

  // Edge Detect Vertical (y)
  if (y[i] > height) directionY[i] = -1;
  else if (y[i] - size < 0) directionY[i] = 1;
}

function setSpeed(i) {
  // Set Horizontal Speed
  if (directionX[i] === 1) x[i] += speedX[i];
  else if (directionX[i] === -1) x[i] -= speedX[i];

  // Set Vertical (y) Speed
  if (directionY[i] === 1) y[i] += speedY[i];
  else if (directionY[i] === -1) y[i] -= speedY[i];
}

function distance(x1, y1, x2, y2) {
  // use Pythagorean Theorem to solve
  // the distance between two Emojis!!!
  let a = x2 - x1;
  let b = y2 - y1;

  let c = sqrt(pow(a, 2) + pow(b, 2));

  return c;
}

function isColliding(emoji1, emoji2) {
  // This function determines whether two
  // emojis are actually colliding! It calls
  // the distance function
  let x1 = x[emoji1];
  let y1 = y[emoji1];
  let x2 = x[emoji2];
  let y2 = y[emoji2];

  let d = distance(x1, y1, x2, y2);

  return d <= size;
}

function fightItOut(emoji1, emoji2) {
  // This function returns what Emoji type
  // the winner is!!!!!
  let emojiType1 = emoji[emoji1];
  let emojiType2 = emoji[emoji2];

  let winner = [
                        // CHRISTMASTREE   SCISSORS   BACON
    /* CHRISTMASTREE */ [CHRISTMASTREE, CHRISTMASTREE, BACON],
         /* SCISSORS */ [CHRISTMASTREE, SCISSORS, SCISSORS],
            /* BACON */         [BACON, SCISSORS, BACON],
  ];

  return winner[emojiType1][emojiType2];
}
```
