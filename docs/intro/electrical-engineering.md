# Electrical Engineering Basics
As many of you already probably know, electricity is used to turn lights on, move motors, and make displays work. The strength of the electricity can be measured in two ways:

 * Voltage: The amount of potential between 2 terminals, usually two poles of a battery. The lower potential is usually labeled as Ground, GND, or - (on a battery). This is measured in Volts.
 * Current: The number of electrons flowing through a circuit per second. This is measured in Amps (A) or more commonly milliamps (mA) because an Amp is very large.

Every component in a circuit also has a resistance. Resistance limits the current flow, and is measured in Ohms or kiloOhms. Obviously, lights, motors, and displays all have resistances, but just plain wires have resistances as well (albeit very small).

If this isn't making any sense at all, that's perfectly fine. To make things easier to understand, electricity is often compared to a water tank:

![Water Tank](https://i.imgur.com/9qGD0xk.png)

Voltage can be seen as the height of the tank, current can be seen as the size of the pipe letting water out, and any bumps or squeezes in the pipe cause resistance. In most cases, you have direct control over voltage and resistance, but not current. This will be explained later.

## Preparing for circuit
Before we start building our first circuit, we should first learn about the different components we are using:

![Arduino](https://i.imgur.com/kBkElOa.jpg)

 * Arduino: By this point, you probably already know what an Arduino is, but here are some things about it you probably didn't know:
     * Has 20 digital Input/Output pins. (digital pins either output 0 volts or 5 volts, never in between. We will go over the other type, analog, later)
     * **Pins can be programmed to either output 5V or 0V.**
         * You can connect stuff to pins, like lights, and program them to turn on, blink, etc.
     * Each pin can provide 5 volts at 40 mA

![Breadboard](https://i.imgur.com/FiP38yn.jpg)

![Breadboard Example](https://i.imgur.com/Ggwtjyj.jpg)

 * Breadboard: A breadboard is used for creating circuits easily. They are very easy to use, you just plug wires into the holes. They are also great for prototyping circuits, but not very good for permanent ones.
     * There are also connections under the pins that connect them in a certain way. You can see how the pins are connected below:

![Breadboard Layout](https://i.imgur.com/UMvWkHw.jpg)

Connect the power pins from the Arduino the "power rail" of the breadboard as shown below. This is so that power connections can be done more easily in the future. They won't be too useful in this circuit though, as there will not be too many things requiring power (just the LED).

![Arduino and Power Rails](https://i.imgur.com/dxp63Ft.jpg)

Okay, let's learn about some more components!

 * Resistor: A resistor limits the flow of current, adding resistance to the circuit. It is used almost everywhere in even the most basic circuits. Resistors also come in many different standard resistances. They use a very special color coding scheme. [Here](https://www.wikihow.com/Read-Axial-Lead-Resistors) is an article on reading the resistor band if you are interested.

![LED](https://i.imgur.com/JjDfVis.png)

 * LED: LED stands for Light Emitting Diode. The Light Emitting portion obviously means that it emits light, and the word diode means that electricity only flows one way. This means that when the light isn't shining when you first turn on the Arduino, the LED is most likely backwards and needs to be flipped around. The short wire coming from the bottom is the negative, and the long wire is the positive terminal.
     * LEDs are also commonly used in series with a resistor. If too much voltage is sent to an LED, it will burn out. The 5V the Arduino sends it is definitely waaay to much, so a resistor is needed to lower the voltage before it goes to the LED.
     * LEDs at normal brightness usually take away around 2V, depending on the efficiency and other factors, and operate at 0.015 Amps or 15 mA, ±5mA. If you don't understand this, that's fine. This will come in handy later.

## Circuit Building Time!
Try to make this basic circuit:

![LED Circuit](https://i.imgur.com/jENOg2C.png)

As the photo says, plug the wire going from the LED to the Arduino into pin 13. Also, make sure the long lead of the LED is going towards pin 9, and the short lead towards ground.

Second, Make sure the resistor you use is a 1K resistor. They should be labeled 1K at either the top or bottom of the paper holding the resistors. If you can't see the label or they are all gone, try to find one loose in your kit. The color coding on the resistor should look like this:

![1K Resistor](https://i.imgur.com/FwU0k6B.gif)

Once this is done, congratulations! You have finished your circuit! Hopefully you can see that the electricity comes out from the programmable pin 13, travels to the LED, then the resistor, and then to ground.

## Why 1K?
How did we end up choosing a 1K ohm resistor?

As the voltage to the LED is increased, it gets brighter and brighter, eventually causing it to burn out. LEDs may be able to take up to 2V before burning out.

Unfortunately, the Arduino's pins provide 5V, so a resistor is needed to use up some of the voltage before it gets to the LED. If we want 1V going to the LED, that means we would need the resistor to take up 4V. This can be seen in the diagram below:

![Voltage](https://i.imgur.com/FdCjBT4.png)

After some testing, we found that a 1K resistor gave the best brightness for our LED.

## A Side Note
A lot of times when looking at photos of circuits, they might look like this:

![LED Schematic](https://i.imgur.com/w9IBszw.png)

This simply another way of representing circuits. Engineers aren't always the best artists, so drawing out detailed and colorful circuits like the ones used in this lesson isn't always very easy. In a diagram like the one above, different symbols represent different elements of a circuit. The upside down triangle with a line under it is an LED, the zig-zag line is a resistor (the amount of ohms is normally labeled, in the above example it is 330 ohms), and the three lines at the bottom represent the ground pin on the Arduino. Other electrical components, such as motors, buttons, and potentiometers, have different symbols in a schematic. More about them can be learned in the kit component lessons later.

## The Math
Although an understanding of the material so far would probably be enough for the rest of the course, it is important to understand the math if you want to do any advanced experimentation. However, this is entirely optional.

Fair warning: this might get boring.

Most basic electrical engineering is based off the equation *V = I * R*.

 * *V* = Voltage (Volts)
 * *I* = Current (Amps)
 * *R* = Resistance (Ohms).

To understand the rest, I have to tell you that you've lied to. LEDs don't burn out because they have too much voltage, they burn out because they have too much current running through them. LEDs get their brightness from electrons flowing through them, and as electrons flow by at a greater rate (remember, current is the number of electrons flowing through a circuit per second), the brightness of the LED increases, eventually causing the LED to get so hot it burns out (more like a bright pop, not a fire).

Current can't be controlled directly, and because current is proportional to resistance by the equation *V = I * R*, we can reduce the amount of current by increasing the amount of resistance.

Here's what we know:

 * Our LEDs are happy with around 4 mA, or 0.004 Amps of current.
 * The Arduino outputs around 5V of voltage.
 * The LED has a resistance of around 250 ohms.

The LED's resistance alone isn't enough to reduce the circuit's current to 4 mA.

Using the equation *V = I * R*, we can plug in the voltage supplied by the Arduino's pins and the desired current to calculate *R*, or the total resistance of the circuit required to lower the amperage down to 4mA.

*5V = 0.004A * R*

*R = 1250 Ohms*

Therefore, we need a total resistance of 1250 ohms to reduce the current of the circuit down to 4mA, or 0.004A. The LED already supplies 250 ohms of this resistance, so we need a 1000 ohm resistor to make up for the rest of the needed resistance. This is why we chose the 1K resistor (for those who don't know, putting K at the end of a number means multiplying it by 1000).

Remember this image?:

![Voltage](https://i.imgur.com/FdCjBT4.png)

We can actually prove this correct if we calculate the voltage taken up by each component using *V = I * R*.

 * *V across LED = I of circuit(0.004 Amps) * R of LED (250 Ohms) = 1 Volt*
 * *V across resistor = I of circuit (0.004 Amps) * R of resistor (1000 Ohms) = 4 Volts*

When we add up the voltage across both components, we get *1 Volt + 4 Volts = 5 Volts*, which is the total voltage given out by the Arduino.

That's all of the math for now. If you have any questions, don't hesitate to ask any of the assistants.
