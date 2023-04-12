# Introduction to Circuit Analysis

This text will server as a basic introduction to electric circuit analysis. In this lesson, the following topics will be covered:

* Voltage, Current and Resistance
* Ohms Law

## Voltage, Current and Resistance
A circuit is a path in which electricity flows from a source to a common ground. When analyzing circuits, we often look for values of voltage, current and resistance. To understand what these properties mean, we can use the **water analogy**, as electric circuits behave very similar to water circuits:

* **Voltage** is the the force that drives a cricuit, similar to water pressure. Voltage (V) is expressed in Volts (V).
* **Current** is the flow of the electricity, similar to the flow of water. Current (I) is expressed in Amps (A)
* **Resistance** is just as it sounds, it impedes the flow of electricity. Think of a water pipe that has a small section that is more narrow than the rest of the pipe. This narrow section would provide some resistance to the flow of water. Resistance (R) is expressed in Ohms ($\Omega$)

Both voltage and current can be provided to a circuit through voltage sources or current sources respectively. Resistance is often provided through electrical components, one of which being **resistors** which have the specific purpose of providing a resistance in a circuit.

For circuit analysis, it is important to identify a **common ground** (or just **ground**) within the circuit. Ground is a common "low point" in which all electricity in a circuit flows to.

We will see that all of these values are related, and changing one of the values will result in a change in the others. This relationship is described in **Ohm's Law**.

## Ohm's Law
The equation for Ohm's Law can be written in three different ways (each way can be derived from another using algebra):

* $V=I*R$
* $I=\frac{V}{R}$
* $R=\frac{I}{V}$

## Example 1

The best way to understand how Ohm's law works is too look at examples, so we will analyze two circuits. Let's start with the following circuit, which has one voltage source and one resistor, as well as a ground reference. We will go over each symbol and what they mean as we go.

[image](../../images/circuitsI/001.png)

On the left we have a voltage source indicated by a circle with a positive terminal (on the top denoted by a `+`) and a negative terminal (on the bottom denoted by a `-`). These two symbols are important as they tell us which direction the voltage source will try to push, from positive to negative or from high to low. The `V2` tells us the name of the voltage source, and `5V` indicates the voltage provided by the source, in this case 5 volts.

On the right we have a resistor indicated by the zig-zag line. The name of the resistor is `R1` and it provides a resistance with a value of 100$\Omega$.

Finally, at the bottom we have a ground reference indicated by a triangle. It is worth noting that ground and all points connected to ground through a wire have a voltage of 0 volts.

All of these components and points in our circuits are connected by wires which are indicated by the black lines. It is worth noting that any two points connected by a wire with nothing in between have the same voltage. We often refer to these points as **nodes**, which comes into play later when we analyze more advanced circuits.

To calculate the current through the circuit, we will use Ohm's law and plug in the known values.

$I=\frac{V}{R}$

$I=\frac{5V}{100\Omega}$

$I=0.05A$

We have found that the current is equal to 0.05 Amps, or 50 milliamps (mA).

There is one more important property of this circuit that we will analyze, and that is the **voltage drop** across the resistor `R1`. A voltage drop describes the amount of voltage loss that occurs through out a portion of or an entire circuit. We can see that one side of the resistor is connected directly to the 5 volt voltage source, meaning the voltage at that point is also 5 volts. The other side of the resistor is connected to ground, meaning there are 0 volts at that point. Seeing how we went from 5V to 0V, we can conclude that the voltage drop across this resistor is 5V.

You may notice that we could also caluclate the voltage by using Ohm's Law again.

$V={I}*{R}$

$V={0.05A}*{100\Omega}$

$V=5V$

Although this voltage drop is the same as the voltage source, this will not always be the case, as we will see in future lessons.

## Example 2

Let's analyze a similar circuit, but with a current source rather than a voltage source.

[image](../../images/circuitsI/002.png)

The current source is a circle just like a voltage source, though instead of `+` and `-` indicators, we have an arrow indicating the direction of current flow. The current source is named `I1` and has a value of 500 milliamps or 0.5 amps. Let's calculate the voltage drop across the resistor `R2` which has a value of 100$\Omega$ using Ohm's Law.

$V=I*R$

$V=0.5A*100\Omega$

$V=50V$

## Closing notes

* Voltage and current can be either positive or negative
* A positive current flowing in one direction is equal to a negative current flowing in the opposite direction