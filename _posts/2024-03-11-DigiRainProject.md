---
layout: post
title: Digital Rain Project
tags: cpp coding project
categories: demo
---

For our C++ Programming Module, we were tasked with creating a Digital Rain or _Matrix Digital Rain Project_ in C++

<img src="https://raw.githubusercontent.com/sarahMATU/DigiRainProject/main/docs/assets/images/matrix-rain.gif" width="450" height="350">

## Introduction
So let's define Digital Rain: _Matrix digital rain, or Matrix code, is the computer code featured in the Matrix series._[1] 

So it was first referenced in the movie, The Matrix; created by Simon Whiteley and his Wife, the iconic digital rain sequence has featured in many video games and movies since its debut. The breakdown of what Digital Rain is can be summed up to lines of random characters that are printed in single/multiple lines to create a raindrop effect.

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
which sets the console colour text to red. Ultimately I decided to create a random function to pick the colour. This way it is unique to my project.
```
std::uniform_int_distribution <int> colour(0, 15);
```
There are 16 different colours that the console can set the text to and with this function I can get the distribution function to pick a number for me and later in the code that will set the above function [2].

Number 2 is a little more difficult. I could either type out each character I wanted to use into a vector or use a random distribution function to fill the vector for me. I chose to use the random distribution function to choose my vector of strings. Like the colour function above I am using another distribution function to set the character. Using the static_cast, it takes the ASCII character and converts it to its char equivalent. For instance, if we take 40 in ASCII this equates to '(' which is the open bracket [3].
```
std::uniform_int_distribution <int> u(33, 127);
c[0][i] = static_cast<char>(u(e));
```

and finally...

Number 3, how would I display them? I want single streams of characters, but do I want them falling one after another from left to right, right to left, truly random? There are so many possibilities and any of them is possible. I decided on single streams printing about 9 characters per line, in different coordinates for each line of code.

## Algorithm
Creating an Algorithm to simulate Digital Rain is very interesting. For the Raindrops themselves, I had to find how long I wanted the drops, if it chose the same characters or random if the colours change automatically or have the option of selecting the colour. For my project, I decided to stick with the same characters for the rain and have the colour change for each stream of rain. This way it is good to keep track of each run-through of the nested loops.
```
for (int z = 0; z < 9; z++) {
  GotoXY(x, y++);

  std::cout << c[0][i] << "\t\n";

  if (y >= 28) {
    system("cls");
    y = 1;
  }

  Sleep(10);
}
```
This was the loop that I decided to use. For GoToXY(), I decided to create two more random functions to pick the position on the console of where to start printing and increase the y coord so it prints the line for the length of the first for loop. The first loop decides how long the stream is which means it will print 9 characters and then move on to the next line.

I also set console limits so the console doesn't move when printing. For this, I resized the vector to make a vector for 100 characters for 19 rows. This way the console should not move and start printing on a new section. I also put a rule so that if the characters exceed this the console will clear and start again.

## Problem-Solving
One of the main problems I encountered was getting the vector random. I had issues in the early days of the vector choosing a random character but only printing that character. I sorted that bug and then faced another when trying to figure out how to print multiple lines at one time. I had only been printing the entire vector at once or single lines of random characters. I finally figured it out when calling the print function I wasn't updating the X and Y coordinates so I was only printing in one place. I fixed this by setting the new random x and y coordinates after the line has been printed.

## Modern C++
When thinking about Modern C++ there are a lot of features that can speed up the process of write and building code. I used some Standard library containers such as std:vector to create my group of characters. For the generation of those characters, I used std::default_random_engine to create a random set of numbers which will be converted to their ASCII equivalent. this allows the numbers that are generated to be truly random [4].
```
std::default_random_engine e((unsigned int)std::chrono::system_clock::now().time_since_epoch().count());
```

## References
[1] Matrix Digital Rain (2023) Wikipedia. Available at: https://en.wikipedia.org/wiki/Matrix_digital_rain (Accessed: 11 March 2024).

[2]“How To Change Color Of Text C++ Console Cmd?,” MarketSplash, Aug. 28, 2023. https://marketsplash.com/tutorials/cpp/how-to-change-color-of-text-cplusplus-console-cmd/ (Accessed Mar. 18, 2024).

[3]“ASCII Table - ASCII Character Codes, HTML, Octal, Hex, Decimal,” www.asciitable.com. https://www.asciitable.com (Accessed Mar. 18, 2024).

‌
[4]“7.11.1. average.cpp,” icarus.cs.weber.edu. https://icarus.cs.weber.edu/~dab/cs1410/textbook/7.Arrays/progexample/average.html (Accessed Mar. 18, 2024).
‌
‌

