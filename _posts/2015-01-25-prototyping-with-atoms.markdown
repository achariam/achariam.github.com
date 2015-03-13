---
layout: post
title:  Prototyping with Atoms
date:   2014-01-25 01:09:40
categories: writing
---

What follows is a story about my first experience creating a physical object with a combination of hobbyist electronics and traditional materials found in a typical workshop. I discuss my mindset, approach and provide some helpful links along the way.

## A Tangible Need

Living and creating in a digital world for a long time makes me want to make something tangible. This is not a [sentiment that I alone feel](https://news.layervault.com/stories/32903-hey-dn-lets-make-something-tangible). Something to hold and admire not a series of zeros and ones that might not be wiped out with an ill advised placement of a strong neodymium magnet.

There is a certain sense of satisfaction that comes from creating a finished physical object. That being said, I wrote this story with the intent of chronicling that journey and hopefully provide some assistance to those interested in starting a similar path that might seem daunting.

Almost two summers ago, I had the distinct honor of being a part of a pilot program intended to provide mentorship to children as a part of the [Maker Education Initiative](http://makered.org/makercorps/). The site I happened to chose was the beautiful [Makerspace](http://makerspace.nysci.org) in the New York Hall of Science out in Queens, NY. 

As a part of the program we had unfettered access to the host of tools available at the space which included 3D Printers, CNC Routers, and Laser Cutters. Coupled with a small stipend to purchase electronics we were allowed to build anything we could conceive.

## The Cube

I chose to work on an idea that I had sketched out in 2009. After owning an iPhone, for a couple years I had a hunch that the constant stream of notifications from apps and services would get overwhelming. To fight the constant barrage I thought that there might be a better way to delegate some of the less important notifications through a different medium. The most effective solution I could think off was the low bandwidth medium of colors and light. An ambient obsidian cube that glowed an array of colors for specific reasons.

This was the original abstract:

> *An LED wifi enabled cube that displays ambient information, such as weather, through glowing colors. It will be controlled by both a web and mobile app.* 

> *Ambient notifications sit in-between being notified and not. In the current binary notification system, an invite to play Candy Crush on Facebook gets the same attention as a text message. Users will be able to create their own notification hierarchy.*

I am about to delve into the world of hardware prototyping again and writing about my last project clears a path for the next one.

## Context Switching

The most exciting part of undertaking a project like this is the ability to learn and mix disparate ideas and disciplines like lego blocks to build your idea. 

The best advice for the kind of mindset you have to be in or adapt is aptly summarized by Elon Musk in a recent AMA.

> *”I do kinda feel like my head is full! My context switching penalty is high and my process isolation is not what it used to be.*

> *Frankly, though, I think most people can learn a lot more than they think they can. They sell themselves short without trying.*

> *One bit of advice: it is important to view knowledge as sort of a semantic tree -- make sure you understand the fundamental principles, ie the trunk and big branches, before you get into the leaves/details or there is nothing for them to hang on to.”*

[-Elon Musk](http://www.reddit.com/r/IAmA/comments/2rgsan/i_am_elon_musk_ceocto_of_a_rocket_company_ama/cnfre0a)

If you’re willing to learn and adapt prototyping is great.


## Embracing Constraints

You will never know everything there is to know about a given subject. The best way to learn is by making. In the physical world especially, you accrue knowledge through trial and error. 

For a real world example, Adam Savage of Mythbusters demonstrates [this paradigm in all of his videos](https://www.youtube.com/watch?v=-tUHJnl8qPM&index=18&list=PLJtitKU0CAehsdcybehbPFHObmWsKtQcY). Watching him craft a box or a movie prop is a master class in building physical objects.

Jony Ive, talks about learning by making as well:

> *“The drive each time was to develop something in terms of its form. And of course we know you can't separate form from materials and certain plastics won't do well for certain shapes. Plastic doesn't actually do very well if you want to do thin, thin, thin, flat surfaces. You can't disconnect material from the form. And you can't disconnect the form from the component that goes inside.*

> *One of the things that drives me potty is this idea that you can have a random shape, and then you think let's make this bit in wood and that bit in plastic. And sometimes you see car interior sketches, where, obviously there's form and there's divisions of forms and some lovely colouring in – those boys can do a really good colouring in – and then there are these arbitrary bits of wood. And you think, wood's not that shape. Of course we can make anything any shape, but that's just being bloody minded. You can't make those decisions, you can't read about it, you gain that experience by making.”*

[- Jony Ive](http://www.dezeen.com/2014/11/13/design-education-tragic-says-jonathan-ive-apple/)

## The Build

There is no one definite way to build out an idea. I didn’t have much time to put together a prototype so for the first prototype I wanted to assemble something relatively quickly and easily. There is a host of websites to get electronics and I chose [Adafruit](www.adafruit.com) for the close proximity of their warehouses to the museum. 

Since I  had a small stipend and a simple idea my parts list was relatively sparse. We also had access to a series of basic electronics that included, soldering setups, Arduinos and other prototyping gear. 

- [1m of 5V RGB LEDS](https://www.adafruit.com/products/1461)
- [Raspberry Pi](https://www.adafruit.com/category/105)
- [Wifi Dongle](https://www.adafruit.com/products/814)

If you have no experience with anything electronics related, don’t worry. Ada fruit and other sites like [Sparkfun](https://learn.sparkfun.com) have [comprehensive guides and forums](learn.adafruit.com) on everything that you could possibly need on getting started. Spend sometime reading through these excellent resources before you purchase anything.

Once the parts were delivered I got to assembling my prototype. Since, I had no experience with electronics, I decided to run a strand test on the LEDs with a spare Arduino.

The next step was getting it to work with the raspberry pi. The Arduino is a simpler micro controller whereas the Pi is a full blown tiny computer with some of the lower level capabilities of the arduino. Since all I needed to do was drive LEDs, it made more sense to have a powerful computer manage the logic and data.

Once I had a basic python script written controlling the LEDs, things were starting to look good. Since we’re running a headless linux machine, the Pi is able to do a lot of what you would be able to do on a normal computer. Due to the awesome developer community there are a ton of libraries written in the most popular languages controlling common electronics via a high level language like Python. This saves a ton of time when prototyping. In more advanced prototyping you have the ability of designing custom chipsets and writing byte code but that is outside the scope of this article. Just be aware if you intend on manufacturing your prototype at some point it’s good to take these things into consideration. 

It is not impossible, following the dev blogs of small indie startups gets you a lot of auxiliary information. IoT objects like the Lockitron, google glass, Pebble all started out on hobbyist boards before being designed for a manufacture ready prototype. I was aware of all these and doing active research on a second version of the cube while building this first one. 

For my demo I ended up running a self contained twisted python web server on the PI so I could remotely control the cube over the Local Network. This allowed me to create and serve a local web page that ran three functions. The rainbow strand test, a white remote controlled light switch, and softly glowing notification mode for checking my e-mail.

Once the software was established, came the job of forming the electronics I had into a cube. The way I built it had some severe limitations due to the size of the raspberry pi board and the way the LED strips were manufactured.

To enclose the board I got 3D printed from ABA plastic a mounting structure for the raspberry pi on a clear acrylic plate which I sanded for a frosted diffused effect. There is a site called thingiverse which host open source designs of numerous cool 3D models that anyone can print. The LEDS were cut into strips of 3 and assembled wired into what would become the 5 walls of the cube. Mounting the led cube within a larger acrylic box allowed for the LEDS to be diffused in an aesthetically pleasing way. What I don’t mention but you should be aware off is the fact that while I’m doing all this you’re constantly hitting up against the material limits of whatever you’re using, As Jony said earlier thin plastic could only do certain things and act certain ways. As you experiment with more and more materials you will start learning about the inherent properties of each one.

Creating the mounting structure for the 5 LED walls proved most challenging and I am still not quite happy with it. I ended up 3D printing another harness I found atop the current raspberry pi to hold a wooden dowel that would support a laser cut piece of wood holding the top face of the LEDs. Sugru, a fast drying putty like adhesive, was used to quickly mount this top plate after failing several times with glue.

Once this was done, the cube was almost complete. All that was left was securing the other acrylic shell to the base temporarily. The finished cube was almost entirely different than I had first imagined. But just like software prototypes are iterative and the next version can always be refactored to be better. I am unhappy with a lot of things, but I also learned a ton about the next version I wanted to create.

## Validating Ideas

Two years later and I still haven’t created  version 2 of the cube. After creating the first prototype I realized a number of things, chiefly being that while beautiful there wasn’t enough utility to justify creating a second version. But the only way I could have figured that out is by having and using this prototype for several months. The lessons I learned were innumerable on this project and for that alone going through the act of creating it was hugely beneficial. It was a jumping of point that helped me work with a client who created large scale displays for art. The lessons I learned prototyping helped me create real value in the world. 

Hopefully this lengthy article inspires and helps you in your journey towards making something tangible. Please don’t hesitate to contact me, if there are any mistakes or if you have any questions.

## Helpful Links & Resources

Along the way I’ve collected a bunch links that helped fill in the gaps. I’ve listed the most interesting ones below along with a short description.

Lockitron
Raspberry Pi Controlled AC Unit

Whenever I try to turn an idea into a prototype I try base the materials I need on [first principles](https://www.youtube.com/watch?v=NV3sBlRgzTI). Another trick I gleaned from Elon Musk, who employs this mental model to great effect.

## Advanced prototyping and further reading

Bunny
AliBaba
Wireless Standards
Manufacturing considerations

http://atomicdelights.com
