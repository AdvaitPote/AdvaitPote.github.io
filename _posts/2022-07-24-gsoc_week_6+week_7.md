---
layout: post
title: "GSoC Week 5 and 6"
date: 2022-07-24
excerpt: Summary of the fifth and sixth week of GSoC 2022
tags: [gsoc, Google, OpenSource]
feature: /assets/img/Unknown.png
comments: true
---

<img src="{{site.baseurl}}/assets/img/Sympy.png">

My summer vacations are just about to end and I had to travel back to my college in Mumbai. Hence, I wasn't able to do much at the start of the week. 

However, a minor bug was encountered which Prakhar bought to my attention. During many operations and because of how floats interact & behave, sometimes, instead of getting absolute zeroes as results, one would get terms which would tend to an infinitesimal term. Though close, the result is not equal to zero. 

What I did was just simply find the minimum load applied on the truss and if any of the forces in the `forces_matrix` are less than the `min_load` by more a certain degree, `1E-10` in this case, then that force is just reduced to zero. One cannot simply just reduce the force if it is of a really low order because it wouldn't be correct in the cases where the loads applied are of a low order as well. 

About torsion, I feel that implementing a new class `Shaft` wouldn't be necessary as a provision for torsion is already provided in the `Beam3d` class. When one has to initiliase a beam in 3D, a shear modulus is also be provided. Moreover, on the beam, moments can be applied in all the 3 directions including in the x-direction i.e. out of the beam which is what drives torsion. Hence, I would like to continue in the `Beam3d`class itself. 