# Twisted Lines animation documentation 
## Description ## 
Animation in p5 that generates multiple twisted lines, with the color changing, also it has a button which included some information of how to use this program. when user clink the button, a message will show up to remind user. This program can adjust the background color, with black and white background color.

## Requirements ##
p5
ESCRIPT 2015(ES6)
---
I seperated my code into three parts: **line.js**, **index.js**, and **line.html**
## Usage (Divided by parts)
## Part 1
The first part is line.js, in this part I make a class called "line", in order to make my code be a reusable component.
The following is my code
```javascript
class lines {
    constructor(i, w, h, colors){
        this.i = i = 0;
        this.w = w = 0;
        this.h = h = 0;
        this.colors = colors= [color(255, 0, 0), color(0, 255, 0), color(0, 0, 255)];
        createCanvas(windowWidth, windowHeight);
    }
    setType(){
        this.type = type;
    }
```
## Arguments ##
### constructor(i, w, h, colors)
```
The name of the class is called "line", and it has 4 parameters: "i", "w", "h" and "colors"
"i" is a variable use to change the color and the height. The default value is 0;
"w" is the width of the line. The default value is 0;
"h" is the height of the height of the line, and the default is any;
"colors" is the color of the lines as a array, the default value is [color(255, 0, 0), color(0, 255, 0), color(0, 0, 255)]
```
### setter
```javascript
    setType(){
        this.type = type;
    }
```
```
In order to use the setter, the format is create a setter called set_object_name(value_you_want). Inside the setter, set a value to your property.
I only use 1 setter in order to set the property "type" of the mousePressed, there are two types: 0 or 1, to justify if the user press the mouse or not, and then change the background of the lines.
```

### draw(l) ###
```javascript
   draw(){
        this.type == 0;
        blendMode(BLEND);

        if(this.type == 0) {
            background(255);
            blendMode(EXCLUSION);
        } else {
            background(0);
            blendMode(SCREEN);
        }
        noFill();
        strokeWeight(20);
        for(this.i = 0; this.i < 3; this.i++) {
            stroke(this.colors[this.i]);
            beginShape();
            for(let w = -20; w < width + 20; w += 5) {
                let h = height / 2;
                h += 200 * sin(w * 0.03 + frameCount * 0.07 + this.i * TWO_PI / 3) * pow(abs(sin(w * 0.001 + frameCount * 0.02)), 5);
                curveVertex(w, h);
            }
            endShape();
        }
    }
```
```
This section is the draw section, contain all the object require in order to draw the lines on the screen.
It can also regards as draw object on. p5.Renderer object.
The first thing to do is initialize the tyoe to 0, and then set the blendmode to BLEND.
Then, it mets if else statement, in order to change the background color while the user click the mouse. The default background is black, and the value of "type" is 0, if the user click the mouse, the value will change to 1, and then change the background color to white. Also, change the blendMode to EXCLUSION in order to see the white color clearly. When change back again, the blendMode will change to SCREEN so that the user can see the black color clearly again. nofill() disables filling geometry, so that we can set the strokeWeight to 20. 
There is a for loop, in order to change the color of the line, the for loop will run while the program is running, so whatever the background color is, the color of the line will never stop changing.
At last, use endshape() to CLOSE the shape. So that one revolution is end.
```

### mousePressed() ###
```javascript
    mousePressed (){
        if(this.type == 0) {
            this.type = 1;
        } else {
           this.type = 0;
        }
    }
}
```
```
I use the mousePressed() function to justify the value of "type" in order to change the value, and change the background color. 
If the user click the mouse, then the type will change to 1, and if the user click again, it will go back to 0 again, and the value of type will in [0,1]
```
## Part 2
The **index.js** is the second part of my code, it including the variable which use to use the class and draw function.
```javascript
let l;

function setup(){
    l = new lines();
}

function draw(){
    l.draw();
}
function mousePressed(){
	l.mousePressed();
}
```
```
In this part, first I declare a variable called l, and then create a function called "setup", in order to use my function in line.js file. I use new keyword to assign the class, then I created another function called draw, also created a function called mousePressed, and I use l.draw() and l.mousePressed() in order to called the so that I can use draw function and mousePressed function inside the lines class.
```
## Part 3
The line.html is the third part of my code, in this part, I created a html file in order to use p5 run my javascript code.
```html
<!DOCTYPE html>
<html>
  <head>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.7.2/p5.js"></script>
    <script  type="text/javascript" src="success.js"></script>
    <script  type="text/javascript" src="index.js"></script>
  </head>

  <body>
  	<form>
  		<input type="button" onclick="alert('Notice how the background colour change? Click any part of the screen to toggle the background colour')" value="Click Me!">
    </form>
  </body>

</html>
```
```
In this section, first I created the basic structure of html file, and then, I use type="text/javascript" to tell the web browser the type of the code is javascript syntax.
Also use "src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.7.2/p5.js" to use p5.js online.
Below this line, I link two of my code file using<script  type="text/javascript" src="success.js"></script> and <script  type="text/javascript" src="index.js"></script>, at last, I create a button, when the user click the button, it will show up a message that said "Notice how the background colour change? Click any part of the screen to toggle the background colour", just for a instruction.
```
## LICENSE
twisted lines by aadebdeb https://www.openprocessing.org/sketch/402961

License under Creative Commons Attribution ShareAlike

https://creativecommons.org/licenses/by-sa/3.0/
