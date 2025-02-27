Download link :https://programming.engineering/product/problem-set-1-categorizing-ai-environments/

# Problem-Set-1-Categorizing-AI-Environments
Problem Set 1 Categorizing AI Environments
Q1 Under what (implementation-related) assumptions is maze-solving a fully observable

environment? What are the agent’s percepts?

(2)

Q2 Under what (implementation-related) assumptions is maze-solving a partially ob-

servable environment? What are the agent’s percepts?

(2)

Q3 Is a known environment always fully observable? Explain with an example.

(2)

Q4 Is a partially observable environment always an unknown environment? Explain with

an example.

(2)

Q5 What is the difference between an unknown environment and a non-deterministic

environment? Explain with an example.

(2)

Search1

In this problem set, we will be using Rook Jumping Mazes (RJMs) – a game based on Rook moves in Chess – to understand various search techniques. In an RJM, you are given a square n × n grid, with each cell containing a number between 1 to n − 1. From any cell, the player may move either horizontally or vertically but must take exactly the number of steps as shown on the player’s current cell. Regardless of the length of the jump (i.e. number of cells passed), this action is considered a single jump (i.e., having a cost of 1) for purposes of our search. The objective is to get from an assigned start state to a pre-specified goal state. Consider this example:



The cell D1 is the start state and the cell A2 is the goal state. The shortest solution to this RJM is: [D1, A1, A5, C5, C1, C2, D2, A2]. Such a game lends itself well to the various search algorithms we covered in class.

This section of Problem Set 1 is inspired by Todd Neller’s work presented at EAAI 2010.

Original publication: T. Neller, “Model AI Assignments”, AAAI, vol. 24, no. 3, pp. 1919-1921, Jul. 2010.


Q6 Can both Breadth-First Search and Depth-First Search be used to solve RJMs? Will

both yield the shortest path?

(2)

Q7 Assuming that each jump has a cost of 1, irrespective of the number of cells the rook passes while making that jump, we can use A* search to find the shortest path. Recall from class that A* search requires a consistent heuristic to guarantee an optimal solution. Show that for this problem, the Manhattan distance from any cell to the goal cell divided by (n − 1) is a consistent heuristic, where n is the number of cells in a row/column. In other words, show that

H(node, goal, n) = |nodex − goalx| + |nodey − goaly| n − 1

is a consistent heuristic. Remember that a proof may not rely on a single example, but

instead must hold true in general.

(5)

Q8 Consider the following RJM:



On this maze, using the heuristic from Q7, complete the A* search process shown be-low, starting with Step 2. Terminate your search when the Goal node (cell D4) is popped

from the priority queue. Double check your calculations!

(8)

Initialization:

Priority Queue, PQ = {}

cost = 0

v = NULL

path = []

Priority for B2 = cost + Heuristic(B2) = 0 + 4/3

Push start state (v=B2, priority=4/3, cost=0, path=[]) to PQ

PQ = {(B2, 4/3, 0, [])}


Step 1

Since PQ ̸= ∅, pop by priority (lower is better in this setting, since priority is based on total heuristic cost).

Priority Queue, PQ = {}

cost = 0

v = B2

path = [B2]

Since B2 is not the goal state, continue.

Neighbors of B2 = {D2, B4}

Priority for D2 = cost + wt(B2, D2) + H(D2) = 0 + 1 + 2/3 = 5/3

Priority for B4 = cost + wt(B2, B4) + H(B4) = 0 + 1 + 2/3 = 5/3

New cost for D2 = cost at B2 + wt(B2, D2) = 0 + 1 = 1

New cost for B4 = cost at B2 + wt(B2, B4) = 0 + 1 = 1

Push (v=D2, priority=5/3, cost=1, path=[B2])

Push (v=B4, priority=5/3, cost=1, path=[B2])

PQ = {(D2, 5/3, 1, [B2]), (B4, 5/3, 1, [B2])}

Step 2, . . . : TODO

Local Search

Your professor is a coffee snob, and since he knows a thing or two about AI, he tries to build an espresso machine that will learn a user’s preferences over time to pull the perfect shot. He lets the machine control the following values:

Weight of coffee beans (15-21 grams)

Grind size (250-400 microns)

Water Pressure (7-11 bars)

Brew time (27-33 seconds)

Sidenote: There was a kickstarter project in 2016 that proposed something similar and failed spectacularly. Link to story.


Q9 Based on our discussions in class, is this problem well-suited to local search algo-

rithms? Explain your reasoning.

(2)

Q10 How you would implement such a program? What would be a reasonable objective function? (This question is somewhat open-ended, so don’t worry too much about the ‘right’ answer. I am really looking for whether your thought process reflects a solid under-

standing of how local search works.)

(2)

Q11 Which of the optimizations and local search variants discussed in class (random restarts, varying step size, simulated annealing and genetic algorithms) are applicable to

this problem, and why?

(2)

Adversarial Search

Q12 Construct a game tree example with a depth of 4 and a branching factor of 2, that illustrates the best-case for alpha-beta pruning, except for the trivial solution. Hand drawn figures accepted for this question, but please ensure clarity. (Here’s some inspiration:

CS151, 2005. Jim Marshall, SLC)

(2)

Q13 Why is it desirable to combine iterative deepening with alpha-beta pruning from a

practical standpoint?

(2)

Academic Integrity

Q14 Review, and copy/paste the following academic integrity acknowledgement in your final submission as the answer to Q14:

I have read and understood the academic integrity policy as outlined in the course syl-labus for CS4100. By pasting this acknowledgement in my submission, I declare that all work presented here is my own, and any conceptual discussions I may have had with classmates have been fully disclosed. I declare that generative AI was not used to answer any questions in this assignment. Any use of generative AI to improve writing clarity alone is accompanied by an appendix with my original, unedited answers.
