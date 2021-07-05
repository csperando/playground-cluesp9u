# Basic Concept

Lets say you want to solve a maze. You start at the beginning and follow a particular path until you reach a dead end. Then what do you do? Obviously there are several ways to solve a maze, but I will explain a particular strategy for the sake of introducing the backtracking algorithm. In order to solve the maze, we will keep track of every intersection we encounter, and the direction we chose to take. If we get to a dead end, then we will restart the maze at the last intersection that we encountered. If there are no options left at that intersection, then we will have to backtrack even further to the intersection before that. Eventually, if we follow this procedure we will arrive at the end of the maze. This is illustrated below.

![maze6](https://user-images.githubusercontent.com/33202952/124016802-04a20600-d9b4-11eb-9295-1f8cae5809db.png)

In order to solve this maze, every time we arrive at an intersection we will prioritize our turns in the following order: Left, Straight, and then Right. The first intersection is right at the start of the maze, and we have two options (left or right). Using our pre-defined priorities we will go left first. This will lead us to our second intersection with options left or straight. Going left, we are immediately met with another intersection (number 3) with the same two options. If we go left, then we will arrive at the first dead end in our quest to solve this maze.

![maze7](https://user-images.githubusercontent.com/33202952/124018123-8181af80-d9b5-11eb-8b47-d7656fca1119.png)

At this point we will have to go back to our last intersection (number 3). Now that we have already tried going left, the only option available to us is to go straight. However when this is attempted we reach another dead end. Starting over at intersection number 3 we realize that we are out of options, which means we will have to **backtrack** to the previous intersection (number 2).

![maze8](https://user-images.githubusercontent.com/33202952/124019184-b80bfa00-d9b6-11eb-814e-a46a07cb0b2f.png)

Once again we have reached a dead end and our options at intersection number 2 have run out, so we backtrack to intersection 1. 

![maze9](https://user-images.githubusercontent.com/33202952/124130628-fd7b0680-da4c-11eb-8dea-434a3e28db1d.png)

Then, after going straight at our fourth and final intersection, we have reached the end of the maze. success!

![maze10](https://user-images.githubusercontent.com/33202952/124131206-90b43c00-da4d-11eb-9c14-c90d3cd82e0b.png)

For most human beings it does not take much more than a moment to identify the correct path through this maze. Most of us also would not "test" going left and backtracking after dead ends either. However, this demonstrates a basic backtracking algorithm that you could make in order to solve any maze regardless of its complexity. 

## The Algorithm (Pseudocode)

First, what values did we need to keep track of in order to solve this maze? First we stored the positions of each intersection. Next we determined what options we had at each intersection, and finally the direction(s) we chose to take at each intersection.

What we also had to calculate (although not explicitly stated) was our own position as we traversed through the maze. So essentially our algorithm works a little as follows.

```python

  intersections = []
  
  while(unsolved):
    userPosition = (row, col)
    
    options = []
    getOptions(userPosition)
    
    if( number of options is zero):
      # dead end reached
      backtrack()
    
    elif( number of positions is one):
      # continue
      
    else:
      # intersection reached
      intersections.append(userPosition, options)
  
```

What does this backtracking function actually do? 

# Why 'if' Statements Will Not Work

When implementing a backtracking algorithm recursion is almost always necessary. If you try to backtrack by using if-statements, then there is a very good chance that after a certain depth your algorithm will trap itself in a loop. 

```python
  if( no more options at intersection):
    # go back to previous intersection
    
    if( no more options at this intersection either):
      # go back to previous
```

# Example Solution

Below is an example of a backtracking algorithm that can be used to solve this maze. The maze is provided as an input using a text file ```input.txt```. "**#**" characters represent the maze borders, "**-**" represent open moveable spaces, and the "**S**" and "**E**" characters represent the start and exit positions respectfully. 

```
input.txt
    # # # # # # # # # # # # # # # # # # # # #
    # - - - - - - - - - # - - - - - - - - - E
    # # # # # # # # # - # - # # # # # # # # #
    # - - - - - - - - - # - - - - - - - - - #
    # - # # # # # - # - # - # - # # # # # - #
    # - # - # - # - # - # - # - # - # - # - #
    # - - - # - - - # - - - # - - - # - - - #
    # # # # # # # # # # S # # # # # # # # # #
```

```python
# os is required for file input/output
import os

# use open() on the desired text file to make iterable
path = "C:\\Path\\To\\Maze\\Input\\"
inputFile = open(path + "input.txt", "r")

# variable for storing maze info
maze = []

# iterate over every row of the input text file
# some string manipulation may be needed to remove end-of-line characters
for row in inputFile:
    line = row.split(" ")
    line[len(line)-1] = line[len(line)-1][:1]
    maze.append(line)

# always use close() after opening a file for i/o
inputFile.close()
```

For more information on using files in python see: [File I/O in Python](https://www.google.com/?q=file%20i/o%20in%20python)

# Famous Puzzles for Backtracking Practice

The 8-Queens, sudoku, etc.

# Additional Links

* [Basic Recursion in Python](https://tech.io/playgrounds/58025/basic-introduction-to-recursion-in-python)
* [File I/O in Python](https://www.google.com/?q=file%20i/o%20in%20python)
