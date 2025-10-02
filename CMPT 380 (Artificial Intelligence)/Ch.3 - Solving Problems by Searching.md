## Reflex Agent
- Actions are a direct mapping from their state.
- Can't work well in environments
	- Mapping takes up too much storage.
	- Takes a long time to learn.
- A goal-based agent works better here.
## Problem-Solving Agent
- A variant of goal-based agent.
- Solves problems by finding sequences of actions leading to desirable goals.
- First step of problem solving is making a goal.
## Goal Formulation
- Goal is formulated as a set of world states wherein the goal is satisfied.
- Actions are the operators which take the agents from its initial state to its goal state.
## Problem Formulation
- This is the process of deciding which actions and states to consider.
## Search
- There are many ways to express a goal, so we express them as a **tree**.
- Multiple options of unknown value to get to a point.
- We use various search algorithms to travel through the tree to the goal.
- The best sequence is called the **solution**.
## Well-Defined Problems & Solutions
- A problem is defined by five components:
	1. **Initial State**: Where the agent starts.
	2. **Action Set**: What the agent can do.
	3. **Transition Model/Successor**: Description of actions, and the states they can reach.
	4. **State Space**: Initial state, actions, and transition model.
	5. **Path**: Within the state space, what sequences of states connected by actions are there?
- We use a **goal test** on each state to test if the agent has reached its goal.
- **Path Cost** functions assign numeric cost to each path.
- The **optimal** solution is the one with lowest path.
- **Abstraction**
	- A process to take out any irrelevant information from states and actions.
	- Leaves the most essential parts to the description of the states.
	- Removes detail from representation.
	- Only the most important parts that are contributing to searching are used.
# Chapter 3 Notes

## Reflex Agent

- base actions on a direct mapping from states to actions
- cannot work well when mapping is too large or slow to learn
- replaced by goal-based agent in complex environments

## Problem-Solving Agent

- a kind of goal-based agent
- solves problems by finding sequences of actions leading to goals
- first step is goal formulation based on current situation

## Goal Formulation

- define goal as the set of world states where conditions are satisfied
- transitions from initial state to goal state require actions
- actions are abstract operators (e.g., “turn left” vs “turn left 30°”)

## Problem Formulation

- decide which states and actions to include
- example: driving from TWU to Maria’s Gelato
    - states: locations along the route
    - actions: turn left, turn right, go straight, accelerate, brake

## Search

- express possible ways to reach a goal as a **tree** of states
- examine different action sequences to choose the best
- a search algorithm takes this problem and returns a solution (list of actions)
- agent design pattern: formulate → search → execute

## Well-Defined Problems & Solutions

- a problem consists of:
    1. initial state where the agent starts
    2. action set the agent can perform
    3. transition model (successor function) describing results of actions
    4. goal test to identify goal states
    5. path cost function assigning numeric cost to each path
- state space: all states reachable from the initial state
- solution: path from initial state to a goal state
- optimal solution: minimum path cost

## Abstraction

- remove irrelevant details from state and action descriptions
- keep only essential information needed for search

---

## Example Problems

### Vacuum World

- states: dirt/clean in each location + agent position
- actions: left, right, suck, no-op
- goal: all locations clean
- path cost: 1 per action

### 8-Puzzle

- states: positions of eight tiles and blank in a 3×3 grid
- actions: move blank up, down, left, or right
- goal test: match the goal configuration
- path cost: number of moves

### 8-Queens

- place eight queens so none attack each other (row, column, diagonal)
- goal test: no two queens threaten each other
- path cost: zero
- formulations:
    - incremental: add one queen at a time (≈1.8×10¹⁴ sequences)
    - complete-state: one per column, move them until safe (≈2 057 states)

### River Crossing

- items: man, wolf, cabbage, chicken
- constraints: wolf eats chicken; chicken eats cabbage; boat carries man + one item
- goal: all items safely across

---

## Environment Types

- static, fully observable, deterministic, sequential, discrete

## Real-World Problems

- airline route finding
- traveling salesperson (NP-hard)
- VLSI layout
- robot navigation
- automatic assembly sequencing

## Complexity Classes

- **P**: decision problems solvable in polynomial time
- **NP**: “yes” instances verifiable in polynomial time
- **NP-Complete**: hardest problems in NP; every NP problem reduces to any NP-Complete problem in polynomial time
- **NP-Hard**: at least as hard as NP-Complete; need not be decision problems or in NP

### Knight’s Tour

- sequence of knight moves visiting every square exactly once
- open tour: does not end one knight’s move from start
- closed tour: ends one knight’s move from start

---

## Search Trees

### State Space vs Search Tree

- state space: unique world configurations
- search tree: nodes represent paths; same state may appear multiple times

### Search Node Components

- **STATE**: world state of the node
- **PARENT**: node that generated this node
- **ACTION**: action applied to parent
- **PATH-COST** (_g_): cost from the initial state to this node

### Fringe (Frontier)

- set of generated but unexpanded nodes
- implemented as FIFO queue, LIFO stack, or priority queue depending on strategy

---

## Data Structures for Search

- **Queue** (FIFO) for breadth-first search
- **Stack** (LIFO) for depth-first search
- **Priority Queue** ordered by path cost or evaluation function

---

## Measuring Problem-Solving Performance

- **Completeness**: guaranteed to find a solution if one exists
- **Optimality**: guaranteed to find least-cost solution
- **Time Complexity**: number of nodes generated (function of _b_, _d_, _m_)
- **Space Complexity**: maximum nodes stored in memory
- parameters:
    - _b_: maximum branching factor
    - _d_: depth of shallowest goal
    - _m_: maximum depth of state space

---

## Uninformed Search Strategies

### Breadth-First Search (BFS)

- expands all nodes at depth 0, then depth 1, and so on (FIFO fringe)
- complete if _b_ is finite
- optimal if all step costs = 1
- time & space: O(_b_^{d+1})

### Uniform-Cost Search (UCS)

- expands node with lowest path cost _g(n)_ (priority queue)
- complete & optimal with nonnegative step costs
- time & space: O(_b_^(1+⌊C*/ε⌋))

### Depth-First Search (DFS)

- expands deepest node first (LIFO fringe)
- space: O(_b_ × _m_)
- not complete in infinite spaces, not optimal

### Depth-Limited Search

- DFS with a maximum depth _k_
- outcomes: solution, failure, or cutoff
- complete if _k_ ≥ depth of solution

### Iterative Deepening Search (IDS)

- repeated depth-limited searches with increasing limits (0, 1, 2, …)
- combines DFS space efficiency with BFS optimality
- complete & optimal for unit costs
- time: O(_b_^d), space: O(_b_ × _d_)

### Iterative Lengthening Search (ILS)

- like IDS but uses path-cost limits (uniform-cost cutoff)
- reduces memory need compared to UCS
- incurs extra overhead

### Bidirectional Search

- simultaneous forward search from initial state and backward search from goal
- time & space: O(_b_^(d/2))
- challenges: defining backward operators, storing both frontiers

---

## Avoiding Repeated States

- cycle checking: reject successors equal to parent
- ancestor checking: reject states matching any ancestor
- closed list (explored set): reject any state already expanded or in the frontier

---

## Summary

- a well-defined problem: initial state, actions, transition model, goal test, path cost
- search transforms problem into tree or graph exploration
- uninformed methods trade off completeness, optimality, time, and space:
    - BFS, UCS, DFS, depth-limited, IDS, ILS, bidirectional search