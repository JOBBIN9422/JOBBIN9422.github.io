---
title: Snake AI
layout: default
---
<figure>
  <img src='images/greedy.gif'/>
  <figcaption>Greedy BFS finding a path from the snake's head to the food each time it eats.</figcaption>
</figure>
		 
## Summary
This project showcases several pathfinding algorithms which I implemented for the sake of automating a game of *Snake*. I wrote the game in C++ using the FLTK library for graphics and user input. The following pathfinding algorithms are included:
- A-Star
- Greedy Best-First Search
- Breadth-First Search
- Depth-First Search

### Legend
Each algorithm's search is drawn on the game field with the following color scheme:
<ul>
  <li><strong><font color='blue'>Blue: </font></strong>Nodes which have already been explored (closed set).</li>
  <li><strong><font color='cyan'>Cyan: </font></strong>Nodes which are currently being explored (frontier/open set).</li>
  <li><strong><font color='red'>Red: </font></strong>The path selected by the algorithm.</li>
</ul>

### Algorithms
<figure>
  <img src='images/astar.gif'/>
  <figcaption>The <strong>A-Star algorithm</strong> uses a heuristic function to evaluate nodes 
			  and prioritize them based on their goal distance and distance from the starting node.</figcaption>
</figure>

<figure>
  <img src='images/bfs.gif'/>
  <figcaption><strong>Breadth-first search</strong> radiates outward in all four directions - it evaluates all of a given node's
			  neighbors before proceeding outwards. This has heavy performance implications due to its
			  poor space complexity.</figcaption>
</figure>

<figure>
  <img src='images/greedy.gif'/>
  <figcaption><strong>Greedy best-first search</strong> works in the same manner as A-Star
			  but with a different heuristic which only prioritizes nodes by their
			  distance to the goal node. This can achieve similar results while exploring
			  fewer nodes.</figcaption>
</figure>

<figure>
  <img src='images/dfs.gif'/>
  <figcaption><strong>Depth-first search</strong> was included mostly as a curiosity since
			  it's ill-suited to this sort of problem. DFS expands all nodes in a given
			  direction from the current node before choosing another path. For this reason,
			  it explores a lot of unnecessary nodes before finding the goal.</figcaption>
</figure>

### Continuous Search
After testing each algorithm for a while, I noticed that paths became more and more convoluted as the snake grew in length. This is because the snake's body becomes  a moving obstacle for the algorithm to path around - the path it initially finds may become suboptimal 
as the snake's body moves out of the way.

To solve this issue, I added the option of re-running the path search on each frame. This allows the snake to re-evaluate its path as its body segments move, leading to better (shorter) paths at the expense of a lot of extra computation.

<figure>
  <img src='images/greedy-repeat.gif'/>
  <figcaption>Repeated searching allows Greedy BFS to 'tighten' its original path around the snake's tail segments.</figcaption>
</figure>

### Statistics
The program tracks various statistics about each run in order to allow for easy comparison of the different algorithms. This gives a better idea about the time and space complexity of each search and allows you to weigh the pros and cons of different shortest-path algorithms.

<figure>
  <img src='images/stats.PNG'/>
  <figcaption>Statistics collected at the end of each run.</figcaption>
</figure>

## Compiling & Running
If you're using a Linux-based OS, check out the [repository](https://github.com/JOBBIN9422/SnakeAI) and use the included makefile. 
For Windows, follow [these directions](https://bumpyroadtocode.com/2017/08/05/how-to-install-and-use-fltk-1-3-4-in-visual-studio-2017-complete-guide/) with the source code from the repository.

<img src='images/options.PNG'/>

The above options work as follows:
- **Time Step (Seconds):** The length of each frame in seconds (default 0.05).
- **Screen Width (px):** The screen width in pixels (default 800).
- **Screen Height (px):** The screen height in pixels (default 600).
- **Search Algorithm:** The pathfinding algorithm used to guide the snake (default A-Star).
- **Repeat Search on Each Frame:** Toggles whether or not to re-evaluate the snake's path on each frame.

## Remarks
I wrote this at a time when FLTK was the only graphical software I knew how to develop in. This library is not a great choice for this sort of work since it's actually a GUI toolkit (the snake segments are actually styled UI boxes!).
A more relevant library such as SDL2 would have been a more reasonable pick. Hindsight is 20-20!

## References
- [Wikipedia](https://en.wikipedia.org/wiki/A*_search_algorithm)
- [Red Blob Games](https://www.redblobgames.com/pathfinding/a-star/introduction.html)
- [Fast Light Toolkit](https://www.fltk.org/)