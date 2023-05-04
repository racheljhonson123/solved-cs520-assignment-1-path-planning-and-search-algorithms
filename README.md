Download Link: https://assignmentchef.com/product/solved-cs520-assignment-1-path-planning-and-search-algorithms
<br>
<h1><span style="font-size: 16px;">This project is intended as an exploration of various search algorithms, both in the traditional application of path planning, and more abstractly in the construction and design of complex objects. You will first generate and solve simple mazes using the classical search algorithms (BFS/DFS/</span><em style="font-size: 16px;">A</em><sup>∗</sup><span style="font-size: 16px;">). Once you have written these algorithms, you will utilize other search algorithms </span><em style="font-size: 16px;">to generate mazes that your initial algorithms have trouble solving</em><span style="font-size: 16px;">.</span></h1>

<h1>1         Part 1: Path Planning</h1>

<strong>Generating Environments: </strong>In order to properly compare these algorithms, they need to be run multiple times over a variety of environments. A <strong>map </strong>will be a square grid of cells / locations, where each cell is either empty or occupied. An agent wishes to travel from the upper left corner to the lower right corner, along the shortest path possible. The agent can only move from empty cells to neighboring empty cells in the up/down direction, or left/right – each cell has potentially four neighbors.

Figure 1: Successful – A path exists from start to finish.

Figure 2: Unsuccessful – No path exists from start to finish.

Maps may be generated in the following way: for a given dimension <strong>dim </strong>construct a <strong>dim x dim </strong>array; given a probability <em>p </em>of a cell being occupied (0 <em>&lt; p &lt; </em>1), read through each cell in the array and determine at random if it should be filled or empty. When filling cells, exclude the upper left and lower right corners (the start and goal, respectively). It is convenient to define a function to generate these maps for a given <strong>dim </strong>and <em>p</em>.

Figure 3: Maps generated with <em>p </em>= 0<em>.</em>1<em>,</em>0<em>.</em>3<em>,</em>0<em>.</em>5 respectively.

<strong>Path Planning: </strong>Once you have the ability to generate maps with specified parameters, implement the ability to search for a path from corner to corner, using each of the following algorithms:

<ul>

 <li>Depth-First (Graph) Search</li>

 <li>Breadth-First (Graph) Search</li>

</ul>

<table width="652">

 <tbody>

  <tr>

   <td width="635"><em>d</em>((<em>x</em><sub>1</sub><em>,y</em><sub>1</sub>)<em>,</em>(<em>x</em><sub>2</sub><em>,y</em><sub>2</sub>)) = <sup>p</sup>(<em>x</em><sub>1 </sub>− <em>x</em><sub>2</sub>)<sup>2 </sup>+ (<em>y</em><sub>1 </sub>− <em>y</em><sub>2</sub>)<sup>2</sup><em>.</em>• <em>A</em><sup>∗</sup>: where the heuristic is to estimate the distance remaining via the <strong>Manhattan Distance</strong></td>

   <td width="17">(1)</td>

  </tr>

  <tr>

   <td width="635"><em>d</em>((<em>x</em><sub>1</sub><em>,y</em><sub>1</sub>)<em>,</em>(<em>x</em><sub>2</sub><em>,y</em><sub>2</sub>)) = |<em>x</em><sub>1 </sub>− <em>x</em><sub>2</sub>| + |<em>y</em><sub>1 </sub>− <em>y</em><sub>2</sub>|<em>.</em></td>

   <td width="17">(2)</td>

  </tr>

 </tbody>

</table>

<ul>

 <li><em>A</em><sup>∗</sup>: where the heuristic is to estimate the distance remaining via the <strong>Euclidean Distance</strong></li>

</ul>

For any specified map, applying one of these search algorithms should either return failure, or a path from start to goal in terms of a list of cells taken. <em>(It may be beneficial for some of these questions to return additional information about how the algorithm ran as well.) </em><strong>Questions:</strong>

<ul>

 <li>For each of the implemented algorithms, how large the maps can be ( in terms of <strong>dim </strong>) for the algorithm to return an answer in a reasonable amount of time (less than a minute) for a range of possible <em>p </em>values? Select a size so that running the algorithms multiple times will not be a huge time commitment, but that the maps are large enough to be interesting.</li>

 <li>Find a random map with <em>p </em>≈ 0<em>.</em>2 that has a path from corner to corner. Show the paths returned for each algorithm. (Showing maps as ASCII printouts with paths indicated is sufficient; however 20 bonus points are available for coding good visualizations.)</li>

 <li>For a fixed value of <strong>dim </strong>as determined in Question (1), for each <em>p </em>= 0<em>.</em>1<em>,</em>0<em>.</em>2<em>,</em>0<em>.</em>3<em>,…,</em>0<em>.</em>9, generate a number of maps and try to find a path from start to goal – estimate the probability that a random map has a complete path from start to goal, for each value of <em>p</em>. Plot your data. Note that for <em>p </em>close to 0, the map is nearly empty and the path is clear; for <em>p </em>close to 1, the map is mostly filled and there is no clear path. There is some threshhold value <em>p</em><sub>0 </sub>so that for <em>p &lt; p</em><sub>0</sub>, there is usually a clear path, and <em>p &gt; p</em><sub>0 </sub>there is no path. Estimate <em>p</em><sub>0</sub>.</li>

</ul>

Which path finding algorithm is most useful here, and why?

<ul>

 <li>For a range of <em>p </em>values (up to <em>p</em><sub>0</sub>), generate a number of maps and estimate the average or expected length of the shortest path from start to goal. You may discard all maps where no path exists. Plot your data. What path finding algorithm is most useful here?</li>

 <li>For a range of <em>p </em>values (up to <em>p</em><sub>0</sub>), estimate the average length of the path generated by <em>A</em><sup>∗ </sup>from start to goal (for either heuristic). Similarly, for the same <em>p </em>values, estimate the average length of the path generated by DFS from start to goal. How do they compare? Plot your data.</li>

 <li>For a range of <em>p </em>values (up to <em>p</em><sub>0</sub>), estimate the average number of nodes expanded in total for a random map, for <em>A</em><sup>∗ </sup>using the Euclidean Distance as the heuristic, and using the Manhattan Distance as the heuristic. Plot your data. Which heuristic typically expands fewer nodes? Why? What about for <em>p </em>values above <em>p</em><sub>0</sub>?</li>

 <li>For a range of <em>p </em>values (up to <em>p</em><sub>0</sub>), estimate the average number of nodes expanded in total for a random map by DFS and by BFS. Plot your data. Which algorithm typically expands fewer nodes? Why? How does either algorithm compare with <em>A</em><sup>∗ </sup>in Question (6)?</li>

</ul>

Bonus 1) Why were you not asked to implement UFCS?

<h1>2         Part 2: Building Hard Mazes</h1>

In the previous section, mazes were generated essentially distributing obstructions at random through the environment. Examining these mazes, you found that certain algorithms had various advantages and disadvantages. In this section, you are going to try to construct mazes that are hard for these algorithms to solve, either in terms of a) the length of the shortest path, b) total number of nodes expanded, or c) the maximum size of the fringe.

One potential approach would be the following: for a given solution algorithm, generate mazes at random and solve them, and keep track of the ‘hardest’ maze you’ve seen so far. However, this search approach necessarily does not learn from any of its past results – having discovered a particularly difficult maze, it has no mechanism for using that to discover new, harder mazes. Every round starts again from scratch.

One way to augment this approach would be a <strong>random walk</strong>. Generate a maze, and solve it to determine how ‘hard’ it is. Then at random, add or remove an obstruction somewhere on the current maze, and solve this new configuration. If the result is harder to solve, keep this new configuration and delete the old one. Repeat this process. This has some improvements over repeatedly generating random mazes as above, but it can be improved upon still. For this part of a project, you must design a <strong>local search algorithms </strong>(other than a random walk) and implement it to try to discover hard to solve mazes. Mazes that admit no solution may be discarded, we are only interested in solvable mazes.

<strong>Questions:</strong>

<ul>

 <li>What local search algorithm did you pick, and why? How are you representing the maze/environment, to be able to utilize your chosen search algorithm? What design choices did you have to make to apply this search algorithm to this problem?</li>

 <li>Unlike the problem of solving a maze, for which the ‘goal’ is well-defined, it is difficult to know when we have constructed the ‘hardest’ maze. That being so, what kind of termination conditions can you apply to your search algorithm to generate ‘hard’ if not the ‘hardest’ mazes? What kind of shortcomings or advantages do you anticipate your approach having?</li>

 <li>For each of the following algorithms, do the following: Using your local search algorithm, for each of the following properties indicated, generate and present three mazes that attempt to maximize the indicated property. Do you see any patterns or trends? How can you account for them? What can you hypothesize about the ‘hardest’ maze, and how close do you think you got to it?</li>

</ul>

<ol>

 <li>DFS

  <ul>

   <li>Length of solution path returned</li>

   <li>Total number of nodes expanded</li>

   <li>Maximum size of fringe during runtime</li>

  </ul></li>

 <li>BFS

  <ul>

   <li>Length of solution path returned</li>

   <li>Total number of nodes expanded</li>

   <li>Maximum size of fringe during runtime</li>

  </ul></li>

 <li><em>A</em><sup>∗ </sup>with Euclidean Distance Heuristic

  <ul>

   <li>Length of solution path returned</li>

   <li>Total number of nodes expanded</li>

   <li>Maximum size of fringe during runtime</li>

  </ul></li>

 <li><em>A</em><sup>∗ </sup>with Manhattan Distance Heuristic

  <ul>

   <li>Length of solution path returned</li>

   <li>Total number of nodes expanded</li>

   <li>Maximum size of fringe during runtime</li>

  </ul></li>

</ol>