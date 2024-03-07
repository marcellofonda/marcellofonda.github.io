---
tag: WIP
---

Can digital oscilloscopes be trusted? With all those integrated circuits, you don't really see what's going on... So I built one myself, using nothing more than diodes, transistors, and resistors. Thus was born DOMINIC: the Digital Oscilloscope Module Including No Integrated Circuits.

<!--more-->

## What I learnt in a nutshell

* A lot about oscilloscopes
* The working of some key electronic components:
    * Transistors, of which I had a rough idea (but my many errors taught me better)
    * Zener diodes, which I didn't know existed before
* Soldering
* Drawing circuits on KiCad
* Experience in testing circuits
* Some of the challenges of managing signals

## The full story

Back in my second Lab course at University, we were measuring the [characteristic curve](https://en.wikipedia.org/wiki/Current%E2%80%93voltage_characteristic) of some P-N junction diodes. 
Since their exponential curve can be roughly approximated as having a threshold voltage, I thought out loud: "maybe we can make a voltmeter by putting many LEDs in series: they would light up in sequence. And if we can make voltmeters, maybe we can make an oscilloscope, too!", to which my good friend replied that he didn't know much about it, but maybe what I was looking for were [Zener diodes](https://en.wikipedia.org/wiki/Zener_diode).

### First sketch

I knew nothing about Zener diodes, so I looked them up, and, that evening, I came up with the drawing of a circuit that looked something like this:

![image of the rough circuit](/assets/dominic/first-circuit.png)

The idea was simple: current flows from bottom-right straight to transistor `T1`, lighting up... something I still had to think about. This would happen until the tension becomes sufficient to breakdown zener diode `Z1`, in which case current would flow past it, powering transistors `T2` and `T3`. The role of `T2` is simply to drain away current from `T1`, shutting it off, while `T3` would light up... something else I still had to figure out. Of course this scheme could be repeated at will. Twice the tension would trigger `Z2`, and three times would trigger `Z3`, and so on.

This was the first building block of DOMINIC, and really the only insight needed for a full oscilloscope: I had just designed a modular voltage-dependent switch with, so far as I knew, a good probability of featuring a satisfyingly linear response. I asked my professor what he thought about it and he redirected me with good hope to our lab technician, who would become my guide for this project. I asked him what resistors to pick; he told me some numbers, and I went off to buy them.

### It could work!

I bought all the components and, after some pain trying to fit everything in my tiny breadboard, I finally came up with a testable piece of hardware:

![breadboard with baby Dominic](/assets/dominic/breadboard1.jpg)

On this crowded breadboard you can distinguish a flipped version of the circuit in the drawing: on row 1 drown their feet `T1` and `Z1`; on row 2 there's `T2`... LEDs complete the circuit: I did figure something out in the end. This baby Dominic whose skyline is a promise of short-circuits was the first voltmeter I ever built. And the clumsiest I ever used, for that matter, but that's not the point of it: it worked!