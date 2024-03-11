---
layout: post
title: Digital Rain Project
tags: cpp coding project
categories: demo
---
# Digital Rain Project

For our C++ Programming Module, we were tasked with creating a Digital Rain or _Matrix Digital Rain Project_ in C++

<img src="https://raw.githubusercontent.com/sarahMATU/DigiRainProject/main/docs/assets/images/matrix-rain.gif" width="500" height="400">

## Introduction
So let's define Digital Rain: _Matrix digital rain, or Matrix code, is the computer code featured in the Matrix series._[1] 

So it was first referenced in the movie, The Matrix; created by Simon Whiteley and his Wife, the iconic digital rain sequence has featured in many video games and movies alike since its debut. The breakdown of what Digital Rain is can be summed up to lines of random characters that are printed in single/multiple lines to create a raindrop effect.

When thinking about this Project idea, I had to do a good bit of research on how I could achieve this effect in C++. I first decided to look into Vectors which could hold my set of random characters which I could then iterate through and print into single strings.
## Design & Test
In Designing this project, I had to think of 3 main components. 
1. What colour did I want my text?
2. What characters do I want to display?
3. How did I want to display them?

Number 1 is easy, there is a command for it 
```
HANDLE console = GetStdHandle(STD_OUTPUT_HANDLE);
SetConsoleTextAttribute(console, 4);
```
which sets the console colour text to red.

Number 2 is a little more difficult. I could either type out each character I wanted to use into a vector or use a random distribution function to fill the vector for me. I chose to use the random distribution function to choose my vector of strings
and finally...

Number 3, how would I display them? Obviously, I want single streams of characters, but do I want them falling one after another from left to right, right to left, truly random? There are so many possibilities and any of them is possible
## Algorithm
## Problem-Solving
One of the main problems I encountered was getting the vector random. I had issues in the early days of the vector choosing a random character but only printing that character. I sorted that bug and then faced another when trying to figure out how to print multiple lines at one time. I had only been printing the entire vector at once or single lines of random characters. I finally figured it out when calling the print function I wasn't updating the X and Y coordinates so I was only printing in one place.
## Modern C++
## References
[1] Matrix Digital Rain (2023) Wikipedia. Available at: https://en.wikipedia.org/wiki/Matrix_digital_rain (Accessed: 11 March 2024). 











Font can be *Italic* or **Bold**.

Code can be highlighted with `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list:

- vectors
- algorithms
- iterators

You can add an impage that has been uploaded to the repository in a /docs/assets/images folder.

<img src="https://raw.githubusercontent.com/sarahMATU/DigiRainProject/main/docs/assets/images/DigiRain.png" width="900" height="300">
