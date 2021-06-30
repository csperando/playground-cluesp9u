# Basic Concept

Lets say you want to solve a maze. You start at the beginning and follow a particular path until you reach a dead end. Then what do you do? Obviously there are several ways to solve a maze, but I will explain a particular strategy for the sake of introducing the backtracking algorithm. In order to solve the maze, we will keep track of every intersection we encounter, and the direction we chose to take. If we get to a dead end, then we will restart the maze at the last intersection that we encountered. If there are no options left at that intersection, then we will have to backtrack even further to the intersection before that. Eventually, if we follow this procedure we will arrive at the end of the maze. This is illustrated below.

![maze6](https://user-images.githubusercontent.com/33202952/124016802-04a20600-d9b4-11eb-9295-1f8cae5809db.png)

In order to solve this maze, every time we arrive at an intersection we will prioritize our turns in the following order: Left, Straight, and then Right. The first intersection is right at the start of the maze, and we have two options (left or right). Using our pre-defined priorities we will go left first.

# Famous Backtracking Problems

The 8-Queens, sudoku, etc.

# Additional Links

No links et
