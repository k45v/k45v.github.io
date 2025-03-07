---
layout: post
title:  Book Notes - The Pattern on the Stone (W Daniel Hillis)
date: 2024-11-09
categories: [booknotes]
---

The book presents computer engineering concepts in engaging ways. The reference to Logo brought back fond memories. Here are a few discussions that I found particularly interesting:

1. Engineering vs evolution  
One weakness of the engineering design process is its vulnerability to complexity. Sufficiently intricate software or hardware systems, like modern operating systems, require the efforts of thousands of individuals. No single person possesses a comprehensive understanding, which can lead to mistakes and inefficiencies. In contrast, evolution has produced the brain, which is more complex than a computer and yet not as fragile. It can tolerate bad ideas, incorrect information and even malfunctioning components (e.g. individual neurons are constantly dying and don’t get replaced. Unless the damage is severe, the brain manages to adapt).

2. In one section, the author explores the idea of applying evolutionary principles to generate software programs, such as sorting algorithms. He shares a personal opinion that the reason he puts faith in a human aircraft pilot is because he trusts the process that created the pilot (major pool of candidates and only the ones who pass the tests qualify). Similarly for programs, an evolved sorting program would likely become more dependable than the first iteration written by a group of programmers.  
I don’t quite agree with this. If the desired output is a sorted list and the available technologies are:  
A) Evolved/trained sorting program  
B) Program written by engineers/mathematicians  
I feel that the **A** would be heuristically correct most of the time and be able to produce the output in a shorter amount of time. With **B**, I expect the first pass to not handle corner cases properly, but once those cases are identified, an entire class of operation/functionality can be added and I’d trust the latter to be more accurate when processing a unexpected data set compared to the former.

3. Baldwin effect: when evolving programs, if evolution relies on multiple steps being performed to achieve an outcome (e.g. bird building a nest), then the program should be given partial credit for being able to do one of the steps otherwise the probability of an evolving program figuring out all the steps is very low.
