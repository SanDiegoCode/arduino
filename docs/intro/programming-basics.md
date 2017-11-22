# Programming Basics
 * Open the Arduino Integrated Development Environment (IDE) and save the sketch as blink. Programs will be referred to as “sketches”. Then type the code seen below.
 * **Don’t just copy and paste, typing it yourself will help you learn.**
 * Connect the Arduino to your computer and press the download button, or hit Ctrl + u. You might need to select the serial port of the Arduino.

```
int led = 9;

void setup()
{
    pinMode(led, OUTPUT);
}

void loop()
{
    //blinks an LED on pin 9
    digitalWrite(led, HIGH);
    delay(500);
    digitalWrite(led, LOW);
    delay(500);
}
```

## Programming 101: Variables
 * Variables store stuff
 * They have a type (what they store) and a name
     * Types include ```int``` (whole numbers without decimals), ```char``` (a single letter), ```boolean``` (a true or false, 0 or 1 bit value), or ```string``` (a "string" of characters, that can form a word or sentence).
 * The ‘=’ sign is an assignment operator. It assigns the value on the right to the variable on the left.
 * eg:
  ```
  int led = 9;
  char something = ‘s’;
  boolean arduinosAreCool = true;
  String name = “John”;
  ```

 * Think of "```int led = 9;```" as "Set led equal to 9"
 * Everytime you use the name of a variable, its value is used.
 * eg.
 ```
 int led = 8;
 pinMode(led, OUTPUT) //is the same as pinMode(8, OUTPUT);
 ```
 * If you use a variable in many places in your code, then changing the value of the variable will change its value everywhere. Plus, the name carries more meaning than just a number

## Programming 101: Comments
 * Single-line comments start with //
 * Comments are not part of the the program; they exist so that people can read them and understand what the program is doing.
 * They are useful for explaining parts of the code to someone who might be reading it
 * A good rule of thumb is to add comments if the code is not very clear, i.e. don’t over-add comments, unless it helps you understand the code better.
 * You can add a multi-line comment as well with ```/* ... */```

## Programming 101: Functions
 * A function groups a bunch of code together and gives it a name, so you can run that code anytime by “calling” the function.
 * A function always has parentheses after its name.
 * ```setup()```, ```loop()```, ```pinMode()```, and others are examples of functions.
 * Functions can take parameters to change the way a function is run. Parameters are always placed within the parentheses
 * ```delay()``` takes 1 argument of type int. That argument specifies how much to delay in milliseconds.
     * ```delay(1000)``` would delay for 1 second.
     * ```delay(500)``` would delay for half a second.
 * A function is defined like this:
 * ```void doSomething(int param) { }```
     * ```void``` is the return type. void means it doesn’t return anything
     * ```doSomething``` is the name of the function
     * Optional parameters can be added inside the parentheses. Their types have to be specified
     * The code that the function runs goes inside the curly braces

## Basic Arduino Sketch
 * Every Arduino sketch must have a ```void setup()``` and a ```void loop()``` function.
 * The ```setup()``` function runs once when the Arduino is first started up.
 * The ```loop()``` function is an infinite loop. It runs forever after the setup() function.
 * You can add other functions as well

## Sketch Review
Let's go over the sketch one more time:
```
int led = 9; //creates a variable named led that stores a number

void setup()
{
    pinMode(led, OUTPUT);
    /*
       The pinMode function sets up a pin as either an input or an output. It
       takes two parameters: the pin to set up (in this case the pin stored in
       the pin variable, pin 9) and the word OUTPUT or INPUT in all caps. The
       pin is outputting electricity to the LED, so it is an output. However, it
       may be an input in other cases if it is necessary to read data from a
       button or other sensor.
    */
}

void loop()
{
    // blinks an LED on pin 9
    digitalWrite(led, HIGH);
    /*
        Writes 5V to pin 9. The digitalWrite function takes two parameters: the
        pin number and whether to output 5V (HIGH) or 0V (LOW) on that pin.
    */
    delay(500); // waits 500 milliseconds, or half a second
    digitalWrite(led, LOW); // Writes 0V to pin 9
    delay(500); // waits 500 milliseconds, or half a second
}
```

Congratulations! You are now finished with the introduction tutorial. If you have any further questions, please ask any of the assistants. We'd be glad to help.
