---
layout: post
title: Building a deep learning rig in 2018
date: 2018-07-07 00:00:00 +0100
description: Which parts did I use for my current computer? # Add post description (optional)
img: building.jpg # Add image post (optional)
tags: [building, deep learning, computer, rig] # add tag
---

- Photo by 贝莉儿 NG on Unsplash


I recently was asked by two people to share my experience about building a deep learning computer in 2018 and since I have a rule stating:
>**when asked twice, write it down**

I am now obligated to write a blog post about the process from a hardware perspective. ;) <br>
First things first, this guide is my personal experience and you might have a different one - that is totally fine. 

Now that we have this out of the way, lets go:<br>

### parts list
GPU - Zotac 1080 TI AMP Extreme <br>
CPU - Intel i7 6850k<br>
RAM - Gskill F4 3200 16 GB<br>
motherboard - AsRock X99 Extreme4<br>
PSU - EVGA 1000 W GQ <br>
case - Corsair Air 740 <br>
CPU cooler - Corsair H115I Pro<br>
SSD - Samsung 960 Pro NVME (512 GB)<br>
HDD - 2x Seagate Barracuda 7200 (4 TB)<br>

### thought process
My thought process evolved around what are the main factors to keep in mind when building such a computational beast.
1. What type and brand of GPU do I need? 
1. What are expected bottlenecks and how to circumvent them
1. Is RAM more crucial than HDD?
1. How many colorful LEDs do I have to endure when building this with current hardware?

The last one is easily the most important so I will start answering this one first:
* some. In my case, both the GPU, as well as the CPU cooler had no other option but to be full of rainbow lighting when powered on - I can live with that. <br>
-> on the plus side, the GPU turns red when used - a nice visual feedback for whether or not your .cuda() is actually working.

**Why did I choose the parts I used? **<br>
I have a bit of bad experience with some hardware brands, which is why I chose some of the brands that worked in my previous computer, build in 2017 (still going strong!)
When building a computer usually the heart is the CPU and its surrounding motherboard, however with deep learning the GPU takes the most precious place and needs to be build around. 

### GPU
In my case I rather quickly decided I wanted a zotac GPU and the 1080 TI is IMO the best performance/price high-end GPU available (http://gpu.userbenchmark.com/ and order by performance, as well as https://blog.slavv.com/picking-a-gpu-for-deep-learning-3d4795c273b9)
The other options are part of the Titan series, which are usually way more expensive and only add an additional GB of memory (11 vs 12 GB).<br>
However, you do not need a 1080 TI necessarily (1060 / 1070 for example are terrific if your dataset does not overflow the available GPU memory). <br>
It's just what I went with ultimately, after careful consideration. 
_be careful about how many slots your GPU needs if you want to use more than 1 GPU - my GTX 1080 TI eats up 2.5 slots, rather big..._

### RAM
Ok, **I had a GPU** and now **chose the RAM next**, this was just a matter of - **DDR4 and max. clock speed for a reasonable price** (I chose 3200).

These parts are interlinked and you might want to aim for at least as much RAM (GB wise) as your GPU has memory (16 vs 11 in my case). 

### SSD & HDD

[Jeremy Howard](https://twitter.com/jeremyphoward) said:
> for storage you want the biggest NVME SSD that fits in your budget

which is why I chose the 512 GB NVME Samsung SSD. Additionally, I read up on compatibility between NVMEs and Ubuntu 16.04 (which is my OS of choice for this computer) <br>
and found many positive reviews on amazon concerning this specific interaction. <br>
The data for my current project will be stored on this harddrive, while long-term storage is mediated by a raid-enabled 4 TB HDD. <br>
(I chose Seagate because they were affordable and I already have two of these at home, running for 2+ years without a glitch.)

### CPU

The CPU is usually not the most important part of a deep learning computer, however it should support 8-16 PCIe lanes per GPU and another 8 for the NVME. <br>
I wanted to first only buy 1 1080 TI but still have the option to add at least another one (for parallel experiments/training sessions) in the near future. <br>
I ultimately did the following calculation: 
> **PCIe lanes needed: 16 for each GPU (32) + 8 for NVME = 40**

Which lead me to an i7 6850k. _Possibly, I might choose an AMD threadripper for the next computer._

### motherboard

The CPU dictates what type of motherboard (socket - in my case LGA 2011-3) you have to choose and then its all a matter of preference. <br>
_I like AsRock boards and the blue color of north/south bridge cover did fit my aesthetic needs._
Technically, I chose this board because of the option to install lots of RAM (up to 128 GB), as well as 3 16x PCIe slots, <br>
the compatibility between the NVME and the board, as well as its capability to fit into the case I wanted.

### power supply unit

First of all, go for the highest quality you can get (gold/platinum or something similar) - otherwise you are burning money for nothing but warm air <br>
(running at its limits the rig can also be used as a space heater...) <br> 
I used the following logic to decide how many Watts I need: 
250 W per GPU + an additional 250-300 for HDDs/CPU/other elements + some buffer -> 1000 W was the sweet spot.

### CPU cooler

I thought about getting a liquid cooled option for some time and since there was some budget left I went with it. 
I compared some solutions and ended up going for the Corsair one because of the massive 140 mm fans (silent) and the amazing ratings on amazon.

### case

I have to be honest now - This choice almost caused the project to end in disaster. <br>
**Be careful when buying a case, your GPU might be very large and has to fit into the case...**

I really liked the look of the Nvidia digits devbox (https://developer.nvidia.com/devbox) and ultimately found that the Corsair Air Series is rather similar. <br>
However, my first idea was to buy the 540 and this would have been disasterous, my GPU would have been too large for this case. 
Subsequently, I went with the 740, which also has two chamber air-flow, which disconnects the hot air from the GPU and the PSU - nice to have, I think. <br>
This decision however was not a conscious one and a random "lets go with the big one for once", saved me a lot of trouble.  <br>
Additionally, this case was produced by the same manufacturer as the cpu cooler, had 140 mm case fans preinstalled and there was a high chance of compatiblity between cooler and case (they complement each other perfectly) <br>

### summary 
This whole setup is super silent (our air conditioning is louder than the computer), well isolated, nice to look at, well equipped for upgrades and super speedy. 

If you have any questions, tweet @ me! 

Happy coding! <br>
![picture of the computer](../assets/img/DL_rig.jpg)
