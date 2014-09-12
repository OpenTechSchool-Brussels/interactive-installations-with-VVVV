---
layout: default
title: "Getting to know your canvas"
num: 1
---

This chapter was written by a human, a super proud one.

##a) Drawing circles and polygones, same stuff!##
But still a stuff we need to learn and this will be your first one. Unless you skipped the previous section (you wouldn't be the first), VVVV is a node based tool kit. This means that your basic way of doing things involves nodes. Let's find out which are required to draw a circle.

First of all, we need to select the node we want to add. For that, double click on the left button or your mouse (***NEED A SYMBOLE FOR THAT***), a menu should appear. You can see a long liste of nodes, some "T C F" letters on the side (which are other way of finding your nodeç and some text area. Start typing "segment" and you'll see the list being filtered bits by bits as you enter text. The node we want is "Segment (DX9)", click on it when you see it in the list. When done, you see a gray box appearing on your patch. This is the basic object in VVVV, the core of the nodal principle.

PHOTO (et text à coté, pas en dessous...)

Gorgeous isn't it? And yet it'd be so much better with some rendering... Let's do that. Guess what we need for the render? Yep, another node. The brilltest among us will start seeing a pattern. The node we need is "Renderer (EX9)". Once you find it, click on it to make it appear on your patch. You should see another screen apparing (on top of having a new node on your patch). A beautiful dark color is displayed on it, that some of you might recognise as black. A good start.

Now it's getting serious. We have two nodes. Something to be drawn, and something to be drawn on. What about making everybody happy and connecting them? For that you need the second kind of object in VVVV: the links. It's time to understand what those little gray squares are on top & bottom of the nodes. The gray squares on top of a node are its input. You can feed them values (text, numbers, shapes...) that will be taken into account by the node. The gray square on the bottom are the outputs, the result(s) of your node. Usualy, the output of one node become the output of another one, creating a data flow.

Try to connect the output of Segment to the Renderer. For that, left click on the output pin of Segment (you will see that some pins grow bigger when you cick on a pin, they are compatible pins - you can imagine you should feed text to a node that expect a nulmber). Then click on an input pin of the Renderer node and ... tada!

Well, more like tadish... where is the circle? Where is the love?

Actually Segments allows you to create many shapes, and among them circles. What it does is drawing a part of a regular polygone (triangle, square, pentagones.... to circles when there are a high number of dots). Sounds not very straight forward? Perfect. Because the strenght of VVVV is not in lenghty text explenations but in interaction. We told you that we can connect links to input pins, but if you hover above them, you see a message, which display its type and often its current value. Not only can you feed those pins, but you can also manualy alter them. Just right click on one (that has a current value), and move your mouse (while still pressing your mouse, drag & drop like). See what's happening? The value is changing, and the results is happening in real time. Experiment with the various input pins, see which you can modify, and try to get a thick circle.

PHOTO

