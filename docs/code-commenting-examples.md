# Code commenting examples

## Overview

- We will be using JSDoc syntax:
  - https://jsdoc.app/
  - https://jsdoc.app/howto-es2015-classes.html
- These comments show up as "hints" in VSCode
- If you type `/**` - VSCode will autocomplete a JS comment template for you

## I. ES6 class examples

**Pac.js**
```js
/**
 * Author: Ace Coder
 * Class that displays a Pacman on the screen.
  */
class Pac{
  /**
   * Create a Pac
   * @param {number} x - the x value.
   * @param {number} y - the y value.
   */
  constructor(x,y){
    this.x = x;
    this.y = y;
    this.speed = 1;
    this.halfAngle = random(4,45);
  }

  /**
   * Draw to the screen.
   */
  display(){
    arc(this.x,this.y,100,100,0+this.halfAngle,360-this.halfAngle);
  }

  /**
   * Animate the Pac by changing the arc()
   */
  update(){
    this.halfAngle += this.speed;
    // flip the speed if the mouth is all the way open
    if(this.halfAngle > 45){
      this.speed = -1;
      // flip the speed back if the mouth is almost closed
    }else if(this.halfAngle < 4){
      this.speed = 1;
    }
  }
}
```

**PLabel.js**
```
/**
 * Author: Ace Coder
 * Class that displays a label on the screen.
  */
class PLabel{
  constructor(){
    this.x = width/2;
    this.y = 300;
    this.text = "Pac";
  }

  /**
   * Draw this.text to the screen.
   */
  display(){
    text(this.text,this.x,this.y);
  }

  /**
   * If mouse is clicked nearby, swap the text.
   */
  flipIfNear(x=mouseX,y=mouseY){
    const distance = dist(x, y, this.x, this.y);
    if(distance < 100){
      if(this.text == "chomp!"){
        this.text = "Pac";
      }else{
        this.text = "chomp!";
      }
    }
  }
}
```

## II. **sketch.js** example

**sketch.js**

```js
/**
 * Entry point for p5.js project.
 */
let plabel;
let pac;

/**
 * Called once by p5.js
 * Initializes canvas and global values.
 */
function setup() {
  createCanvas(400, 500);
  angleMode(DEGREES);
  fill("yellow");
  textSize(100);
  textAlign(CENTER);
  plabel = new PLabel();
  pac = new Pac(width/2,150);
}

/**
 * Called periodically by p5.js
 */
function draw() {
  // fill the screen with black
  background(0);
  // display the label and pac
  plabel.display();
  pac.display();
  // animate the pac
  pac.update();
}

/**
 * p5.js event handler.
 */
function mouseClicked(){
  // if the click is near plabel, then flip its text
  plabel.flipIfNear();
}
```

## III. Function that has a `return` value example

```js
/**
 * Add 2 numbers together and return their sum.
 * @param {number} num1 - The first number.
 * @param {number} num2 - The second number.
 * @return {number} The sum of the 2 numbers.
 */
function sum(num1,num2) {
  return num1 + num2;
}
```
