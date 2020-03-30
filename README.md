# touch-sensitive
*a simple face-touch detector*

A circuit designed to sound an alarm when you touch your face. The idea being to train you to do it less often, hence reducing the transfer of infectious microbes from your hands to your mouth/nose/eyes.

Inspired by Dr Daniel Reardon ([Astrophysicist gets magnets stuck up nose while inventing coronavirus device](https://www.theguardian.com/australia-news/2020/mar/30/astrophysicist-gets-magnets-stuck-up-nose-while-inventing-coronavirus-device)). *I'm under lockdown in Italy so can understand how strange experiments might occur...*

This is a quick-and-dirty proof of concept, essentially a magnet-coil movement detector. The sensor has two parts: a small coil hung around the user's neck, and a small magnet taped to their wrist. When the magnet moves near the coil, the circuit emits a bleep.

Here's a rough video demonstrating it in action:

[![Touch sensitive demo video](https://img.youtube.com/vi/Q7eCi2-oiOE/0.jpg)](https://youtu.be/Q7eCi2-oiOE)

Here's the schematic:

![Touch-Sensitive Schematic](https://github.com/danja/touch-sensitive/blob/master/media/touch-sensitive-schematic.jpeg "schematic")

Oops, unlabelled - the potentiometer is 100k lin.

The coil in the prototype was 20 turns of wire wrap wire, 4cm diameter (toilet paper tube). The magnet was neodymium 10mm diameter, 3mm deep. A larger magnet and more turns are strongly recommended.

## How it Works

It's pretty much textbook op amp circuitry. 

Any signal from the coil first goes into a low pass filter with cutoff frequency of around 30Hz. This frequency was chosen to remove most mains hum the coil might pick up at 50/60Hz. The filter has some gain - probably 10, but I can't remember the Q/gain interaction in this circuit, it might be quite peaky at 30Hz.

The next op amp acts as an inverting amplifier with a gain of about 50. If there's any high frequency instability, a small capacitor (say 100pF) in the feedback loop of this should help. 

This is followed by a half-wave rectifier to effectively follow the peak amplitude of the signal. (Hah! I forgot to add a smoothing capacitor - that would probably improve behaviour).

This LF DC*-ish!* signal is then feed to a 2N7000 MOSFET that is configured as a crude switch/relay. 

The final op amp is an oscillator running at about 1kHz (pulse wave). When the gate of the MOSFET is taken high, the capacitor is shorted out, killing the oscillations. 

The potentiometer should be adjusted to a position where the oscillation is *just* inhibited. 
 
The output level can be fed to a little loudspeaker via a 10u capacitor. (Something like a 100u capacitor would probably be fine too - the op amp output is switching so there shouldn't be much heat generated). For the video I fed the output to some cheap computer speakers.

The circuit is only a first pass, there's plenty of scope for improvement. I didn't play very much as the breadboard got a bit crowded.

![Touch-Sensitive Spaghetti](https://github.com/danja/touch-sensitive/blob/master/media/spaghetti.jpeg "spaghetti")

PS. Oh yeah, the title was inspired by [The Fall](https://www.youtube.com/watch?v=i90EMCj98es) :)








 
