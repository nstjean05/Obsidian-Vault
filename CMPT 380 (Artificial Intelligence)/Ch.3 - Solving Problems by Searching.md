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
	4. **State Space**: Initial state, actions