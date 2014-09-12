---
layout: default
title: "Spread and retract"
num: 2
---


This section was luckily created through random character generation. 

##a) The many and the one

I'm not your parent but yet let me tell you that you should clean your room. This habit of leaving everything on the ground for easy access is not really worth walking upon a lego bricks in the middle of the night... Yes. The room was a metaphor for the patch. A nice way to clean is to arrange stuff in cases that are fit, that's what we're going to do here and create sub-patches. Those are nodes that you'll create yourself. Select a part of your patch by clicking and making a selection zone, and once many nodes are selected, just click *Ctrl-G*. You'll see that the whole group of node became one lone node. The input pins and output pins are still coherently named, and if you're not satisfied by the name of the node, you can always *Ctrl-I* on it and change its name. In order to see its inside, just double right click on it, you can still make modification of this sub-patche if you want to update it. Be careful tho, don't close with *Ctrl-W* (risk losing everything) but close with *Alt-3*. Usually the input and output pins that are created are the one you want, but if you want to add or delete some, just add some **IOBox** (as a feed or as a result of the patch) or delete the one that are already here.

Easy isn't it? Sub patches are very powerful design pattern that not only allows you to clean your patch, but also repeat easily part of it, it's really the equivalent of functions in the coding world. We'll see in a few seconds something that makes it even more powerful.

##b) The one and the many

Okay, now we're talking. Why simplifying stuff? To complexify them later of course. What if you don't want one circle, but many of them? Before you had to redo your whole code node by node. You could have copy pasted it, but it'd have been a mess to update and look at. So you could have done sub-patches. And have many many sub-patches, depending on how many circles you want to have. Or you can just add one more node, and have as many of them as you want, by using spread. Up until now, you might have seen each link as a single road, linking unique object among each others. But nodes are defining types of object, and links are more like highways. Spread allows us to move as many instances on the node as we want on this highway. All in all, a spread will instantiate your node with varying input, and all the rest of your patch will work as fine as before, feel the previous unique node now a list of node.

Let's try this simple example. Create another **Transform**, **Segment** and **Renderer** chain. Put the *Inner Radius* of the **Segment** close to one. And then create a **Linear Spread** and connect its output to *Translate X* of **Transform**. That means that we will instantiate many **Transform** with various *Translate X*, hence many **Segment** with different X offset, and then render them. We now need to specify the range of value and their number. Being a linear, this spread will fit values around a value with a specific width. The *Input* is that reference value, *Width* is the range of the spread, and most interesting to us is *Spread Count* that defines the number of instance. Right click on it and move the value up, I promise you you'll understand more clearly what a spread is! 

In the context of this workshop, we'll be specifically using **Circular Spread** which is linear but ... along a circle. Try it out on our previous simple example, and then apply it to our current project (only difference here is that instead of having one output value, we have two, *X* and *Y*, varying along a circle).

