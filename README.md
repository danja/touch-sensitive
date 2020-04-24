# touch-sensitive
*a simple face-touch detector*

A circuit designed to sound an alarm when you touch your face. The idea being to train you to do it less often, hence reducing the transfer of infectious microbes from your hands to your mouth/nose/eyes.

Inspired by Dr Daniel Reardon ([Astrophysicist gets magnets stuck up nose while inventing coronavirus device](https://www.theguardian.com/australia-news/2020/mar/30/astrophysicist-gets-magnets-stuck-up-nose-while-inventing-coronavirus-device)). *I'm under lockdown in Italy so can understand how strange experiments might occur...*

This is a quick-and-dirty proof of concept, essentially a magnet-coil movement detector. The sensor has two parts: a small coil hung around the user's neck, and a small magnet taped to their wrist. When the magnet moves near the coil, the circuit emits a bleep.

Here's a rough video demonstrating it in action:

[![Touch sensitive demo video](http://img.youtube.com/vi/VTOSdUihxfs/0.jpg)](https://www.youtube.com/watch?v=VTOSdUihxfs)

Here's the latest schematic:

![Touch-Sensitive Schematic](https://github.com/danja/touch-sensitive/blob/master/media/new-schematic.jpeg "schematic")

Note that I had a breaking error in the previous schematic, the resistor on the input of the amplifier stage was labelled as 22k when in fact it was 220R. I misread the colour code.

Coil is 200 turns of 0.5mm enamelled copper wire, approx 10cm diameter.

## How it Works

It's pretty much textbook op amp circuitry. 

Any signal from the coil first goes into a low pass filter with cutoff frequency of around 30Hz. This frequency was chosen to remove most mains hum the coil might pick up at 50/60Hz. .

The next op amp acts as an inverting amplifier with a gain of about 500. If there's any high frequency instability, a small capacitor (say 100pF) in the feedback loop of this may help. 

This is followed by a half-wave rectifier to effectively follow the peak amplitude of the signal.

This LF DC*-ish!* signal is then feed to a 2N7000 MOSFET that is configured as a crude switch/relay. 

The final op amp is an oscillator running at about 1kHz (pulse wave). When the gate of the MOSFET is taken high, the capacitor is shorted out, killing the oscillations. 

The potentiometer should be adjusted to a position where the oscillation is *just* inhibited. 
 
The output stage is a transistor acting as a switch. This drives a salvaged 2" (?) speaker.

## Construction

I knocked the circuit together on a small piece of stripboard. A DPDT switch controls the power with an LED and (2k2?) resistor as on indicator.

I screwed a scrap of aluminium sheet to the output transistor as a heatsink, although this almost certainly wasn't essential. 

![Circuit Board](https://github.com/danja/touch-sensitive/blob/master/media/stripboard.jpeg "Circuit Board")

In this version I made the coil from 200 turns of 0.5mm enamalled copper wire (salvaged from an old transformer). It's on a former made from 3 circles of acrylic sheet, 2 outer approx 10cm diameter, inner maybe 9cm, glued together. It has a length of fencing wire around the outside to protect turns and allow hanging, held in place with epoxy. The whole thing spray-painted and connected to the unit with a 3.5mm jack plug/socket via some 2 core power cable.  

![In case](https://github.com/danja/touch-sensitive/blob/master/media/in-case.jpeg "In case")

I had a little plastic box that the component *just* fit into. After drilling I gave it a coat of spray paint. The circuit board is fitted with plastic standoff posts, the loudspeaker hot-glued in place. 

I made this one for a medic friend. I only realised as I was delivering it that I hadn't taken a pic of the finished unit so did that on the street.	

![Finished](https://github.com/danja/touch-sensitive/blob/master/media/finished.jpeg "finished")

It came out rather neater than the breadboard version:

![Touch-Sensitive Spaghetti](https://github.com/danja/touch-sensitive/blob/master/media/spaghetti.jpeg "spaghetti")

PS. Oh yeah, the title was inspired by [The Fall](https://www.youtube.com/watch?v=i90EMCj98es) :)








 
