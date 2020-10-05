---
title: Monolith and pain
date: 2020-10-05 11:05:00 +01:00
---

When you look at large systems, it's generally easy to recognize patterns and just like code level patterns. system-level patterns also greatly impact the overall system.
Monolith systems the entire program is one big specific unit and this is both the strength and weakness of this pattern. 
It is fast, easy but the sheer bulk of the program can get very overwhelming quickly. 
testing, deployment, debugging is a very painful journey and this can take days, weeks, or even months.
this pattern is particularly not advised in an agile environment as this methodology thrives on delivering results very quickly to stakeholders by results that include occasional CHANGES which a monolith system rarely handles well.

The Big Bowl of mud is often the resulting effect of monolith systems. What usually happens is the initial small system which is started as a monolith to solve a specific small problem, (which is usually an efficient solution at that time) gradually evolves to solving more and more problems added by usually implemented by different programmers often haphazardly.
very often due to pressure from the stakeholders, the sunk-cost fallacy kicks in.

>  The original system should really be replaced by one that's organized properly. But people say that they've spent a fortune on the existing system, so they can't replace it.

people imagine that the cost of replacing is the same as building it. The truth is successful companies like Microsoft, Spotify, Facebook, twitter have all replaced their core system several times.  

A lot of people are afraid to touch monolith systems. small changes can cause major problems, and people that eventually work on such systems tend to use workaround solutions which further compounds the problem, eventually creating layers upon layers of chaos.

it is also great to point out that there can and there are properly structured monolith systems existing today. Stakeholders of this system take care of ensuring that the initial structure is constantly maintained no matter who is working on it. No Shortcuts!
With this strategy, time-consuming deployments/changes are inevitable- a small price to pay. 

In all, whatever you decide, choose your pain carefully.
 