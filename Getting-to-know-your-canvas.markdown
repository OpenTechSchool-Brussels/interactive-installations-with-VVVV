---
layout: default
title: "Getting to know your canvas"
num: 1
---

No animals were harmed or drugs used in the creation of this section.

##a) Drawing circles and polygons, same stuff!##
But still a stuff we need to learn and this will be your first one. Unless you skipped the previous section (you wouldn't be the first), VVVV is a node based tool kit. This means that your basic way of doing things involves nodes. Let's find out which are required to draw a circle.

First of all, we need to select the node we want to add. For that, double left click anywhere on your patch, a menu should appear. You can see a long list of nodes, some "T C F" letters on the side (which are other way of finding your node) and some text area. Start typing "segment" and you'll see the list being filtered bits by bits as you enter text. The node we want is **Segment (DX9)**, click on it when you see it in the list. When done, you see a grey box appearing on your patch. This is the basic object in VVVV, the core of the nodal principle.


PHOTO (et text à coté, pas en dessous...)

Gorgeous isn't it? And yet it'd be so much better with some rendering... Let's do that. Guess what we need for the render? Yep, another node. The most brilliant among us will start seeing a pattern. The node we need is **Renderer (EX9)**. Once you find it, click on it to make it appear on your patch. You should see another screen appearing (on top of having a new node on your patch). A beautiful dark colour is displayed on it, that some of you might recognise as black. A good start.

Now it's getting serious. We have two nodes. Something to be drawn, and something to be drawn on. What about making everybody happy and connecting them? For that you need the second kind of object in VVVV: the links. It's time to understand what those little grey squares are on top & bottom of the nodes. The grey squares on top of a node are its input. You can feed them values (text, numbers, shapes...) that will be taken into account by the node. The grey square on the bottom are the outputs, the result(s) of your node. Usually, the output of one node become the output of another one, creating a data flow.

Try to connect the output of Segment to the Renderer. For that, left click on the output pin of Segment (you will see that some pins grow bigger when you click on a pin, they are compatible pins - you can imagine you should feed text to a node that expect a number). Then click on an input pin of the Renderer node and ... tadam!

![](assets/Ex01-01.JPG)

Well, more like tadam-ish... where is the circle? Where is the love?

Actually Segments allows you to create many shapes, and among them circles. What it does is drawing a part of a regular polygon (triangle, square, pentagons.... to circles when there are a high number of dots). Sounds not very straight forward? Perfect. Because the strength of VVVV is not in lengthy text explanations but in interaction. We told you that we can connect links to input pins, but if you hover above them, you see a message, which display its type and often its current value. Not only can you feed those pins, but you can also manually alter them. Just right click on one (that has a current value), and move your mouse (while still pressing your mouse, drag & drop like). See what's happening? The value is changing, and the results is happening in real time. Experiment with the various input pins, see which you can modify, and try to get a thick circle.

By the way, the patch might not always look as you want. You can left click on a node and drag & drop it anywhere you want on the patch. You can also use classic *Ctrl-X*, *Ctrl-C* and *Ctrl-V* to cut, copy and past. For navigating history, you can use *Ctrl-Z* and *Shift-Ctrl-Z* as expected. You can also select group of nodes by clicking and creating a selection zone. If you want to delete a link, left click on it, then right click. If you want to delete a node, select it and then press *Delete*. Remember to use that to reorganise your patch so you can make more sense of it.
PHOTO


##b) A bit of movement
So... Where is the circle? Check. Where is the love? Still in process. Let's at least have a bit of life and movement already. The segment node is a kind of graphic primitive, it defines what you draw, but not where you draw it. This is because the "where" can be applied to a lot of different objects, so VVVV have a generic node for that. If you learn how to move a segment you can move anything. For that, we need the node **Transform (2d)**. Double click on it to make it appear. Now we need to apply the output of **Transform** to one of the inputs of **Segment**. Can you guess which one? Try to hover over the input little grey squares of the **Segment** node to see what are the expected type of inputs. The second from left needs a Transform type, let's connect it to it. Nothing happens, what a huge let down... and yet, so many inputs for the **Transform** node. Try to modify those values by right clicking on them and drag & dropping. 

Good, some movement, but movement and animations are not the same things. Right now, we still respond to input from the user. This author have to confess an adoration for one of the super power of computers: random enough number generation, aka chaos. It's the easiest way to add some movement (if not chaos) to your renderer. As always, we'll need a node, it should have been named **Awesome** but instead VVVV kept it simple and named it **Random**. Hover over the output pin and you'll see changing values, yay, potential random animations. Now .... it's up to you. Link the output of the **Random** node to anything, either from the **Segment** node or the **Transform** node and see what happens. You can also use many **Random** nodes. If you don't where to start, connect **Random** to the *Cycles* input pin of **Segment** with its *Inner Radius* set at a value around 1. Chill ..... By the way, if you didn't realise one of the pins of **Segment** allows you to change the colour, now is time to try it out. If you prefer to have a node with those value, you can search for **IOBox** nodes (Value Advanced, String or Colour).

A nice thing in VVVV is that you can connect multiple outputs to inputs. If you want to scale the circle randomly, but both on X and Y with the same value so it keeps on beeing a circle, you can connect the output of **Random** (same node as previous, or another created for the occasion) to both the *X scale* and *Y scale* input of the **Transform** node.


##c) Test mic, one two, one two. Is this on?
Let's awaken the MC in you and open the potential of your mic with the **AudioIn**. Find the node, and add it to your patch. Check the input pins, and especially the last one that should show a microphone hardware, and the first one that is called *Enabled* and that is at 0. It's a classic pin you'll see on many nodes. It only accept two values : 0 (for false) and 1 (for true). So if you actually want to use that node, right click, and glide so that *Enabled* goes to one. You know have your mic, you just need to precise in your patch how you want to read that info. In our case, we want a value that correspond to the amount of sound there is, meaning that we don't care much of the frequency (tonality) of the sound, but its amplitude (its loudness). For that, we'll feed the output of **AudioIn** to the **RMS** node. RMS? Of course my dear, Root Mean Square aka quadratic mean. Who doesn't know that?! Well, I didn't. Wikipedia tells us it's a statistical measure of the magnitude of a varying quantity. Let's agree with wikipedia. In short, the amplitude of the sounds vary a lot, RMS allows us to smooth that value and have one that is coherent over a more human time scale. And once again, best way to get it is to check it out and test it. You can either hover over **RMS** output pin, or feed it, for instance to the *Inner Radius* pin of **Segment**. Not happy of the kind of variation? You can modify the value and make mathematical operation over it (same for the output of **Random** or any other number) with various nodes such as \*, /, - or +. Below is an example of such usage. 

PHOTO USAGE BASIC MATHS

By the way, you've been already using a few nodes. Sometimes it's hard to remember what they exactly do. If you're curious about what a node does, select it and press *F1* if the node is common enough, you'll get a help with an example of usage. Even better, this is a patch, so you can copy past from it if you like what you see!

##d) Segments and its friends. Please vote for a better title.
A tad sad to only have one thing to display, let's add some more stuff on the renderer. By the way, if you want your render stand alone or in the patch window, you just need to press *Alt-1* or *Alt-2* try it up. In order to add things, we need to feed **Renderer** with more inputs. Alas, if it's possible to have many links from an output pin, only one link can connect to an input pin. So, we need something to group multiple input. A fitting name for the action, since the node we need is called **Group**. This node will aggregate as many inputs as you want (on various input pins) and group then into a single output that you can feed another node. In our case, use as input the outputs of both **Segment** nodes and then feed the **Render** node with the now single output of **Group**. 
Using another **Transform** and **Segment** node, connected to the **Renderer** try to create a small disc inside our current circle.

PHOTO WITH RESULTS

Polygons are hella sexy but sometimes you need more, like text. So let's add some lyrics to that landscape. To add some text, you need a node weirdly named **Text**. Woah, so many inputs pins... Okay, explore a bit and experiment with possible values. Remember (especially for the *Text* input of the **Text** node) that you can create **IOBox** and then feed those input pins. Just make sure you use the correct type of **IOBox** (string in the case of the *Text* input). Ok, now we want to add that to the render (you can already try but getting rid of one of the **Segment** on the input pins of **Group**) but there are not enough input pins in **Group** :( So, what to do? Either you can stop the workshop and go home (please don't) or you can press *Ctrl-I* after having selected **Group**. You just opened a menu called *Herr Inspector* (VVVS is German, in case you were wondering). This menu regroups setting of the node you just selected. You can do that on any node you want, in our case we want to modify **Layer Temple Count**, two is not enough, chose a higher value (at least three for those that are following...). In VVVV, quitting is linked with the keyboard short-cut *Ctrl-W*. Now you can add your text. Go test the whole she-bang. 


##e) Command center in the making
We will allow later interesting interaction, but as far as the patch is concerned, classics are a good start. We just heard of **IOBox** and *Ḧerr Inspector*, let's inspect such element... Some parameter are particularly usefull. Among others, *Minimu* and *Maximum* allow you to define a range (put 0 to 1 in order to control an **Enable** pin, nice to stop the random generator on a single value!), for a more sensible display right click on both *Show Value* and *Show Slider* to display slider instead of the value. And don't hesitate to try out the various line of **Slider Behavior** from slider to press button (once again, allowing a nice control of random: fitted on **Enable** it can generate a random value at each press).
Try to explore already all you can do, use the mic and randomness to feed **Text** and its associated potential **Transform**. And take a deep breath, because you're in for a treat in next session, we'll discover the not so dark arcane of VVVV.

