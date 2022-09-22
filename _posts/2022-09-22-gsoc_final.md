---
layout: post
title: "GSoC Final Week and Concluding Note"
date: 2022-09-22
excerpt: Final week of GSoC 2022 and Summary
tags: [gsoc, Google, OpenSource]
feature: /assets/img/Unknown.png
comments: true
---

<img src="{{site.baseurl}}/assets/img/Sympy.png">

The first thing I would like to announce is that I have officially completed my project under GSoC 2022! This is an extremely proud moment and I feel extremely elated to have my hard work rewarded like this. These past few months have been exceptional for me when it comes to learning, making more relationships and of course, doing what I love. I would like to thank SymPy and especially my mentor, Prakhar. He has been around a lot for me and whenever I have had a problem, he was always available. He has also provided valuable suggestions to my work which have done nothing but enhanced my product to the maximum. Hope after this project, we can still remain in contact. Now talking about the final work of my project in the final week and weeks after the final week.

I opened the PR for the `draw` method in the penultimate week of the project. It looked good but Prakhar pointed out that it was looking a little bleak which I agreed with. One thing that I did is replace the plots used in the drawing members with rectangles instead and modified their centers and dimensions appropriately as per their corresponding node coordinates. This increased the thickness of the members making them more visible and better.

I also changed the doctests so the truss visible in the docs is one that is more intricate and which shows the entire usability of the method better.

However, there were many issues with this as well. One was that for some nodes, the members were not aligning perfectly with the nodes like the image shown below.

<img src="{{site.baseurl}}/assets/img/nodes_off.png">

Also, another issue raised by another Open Source Contributor was how one was not able to use units like 'm' or 'mm' from `sympy.physics.units` in the `draw` method, specifically for the coordinates of the nodes. Having a symbol in `t._node_coordinates` does not go down well for the method. I have added a commit solving this today itself. As per his suggestion, I added a dictionary by the name `subs_dict` which the user provided and which contains the relative values for each unit like `subs_dict={'m': 1000, 'mm': 1}`. And a `ValueError` is raised if an inadequate `subs_dict` is given and not every symbol/`Quantity` is covered. 