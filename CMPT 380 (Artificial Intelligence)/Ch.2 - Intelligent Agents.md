## Agents
- An *agent* is anything that can be viewed as perceiving its environment through sensors, and acting upon that information.
- There are both human and robotic agents, both with their own kinds of sensors.
- **Percept:** Agent's perceptual inputs at any one time.
- **Percept Sequence**: The complete history of everything the agent has ever perceived.
- Environment -->Perceive --> Sensors --> Agent Processes --> Actuators --> Act on the environment
## Vacuum-Cleaner World
- The vacuum is in one of two tiles.
- Vacuum know which square it is in, and if there is dirt in that square.
- The vacuum can either:
	- Move tiles.
	- Suck up dirt.
	- Do nothing.
- Vacuum has only one function:
	- If the current square is dirty, then suck.
	- If not, then move to other square.
- This is a simple agent function.
- **Performance measures**
	- Design according to what you want in the environment, not how you think the agent should behave.
## Rationality and Rational Agents
- Rationality at a given time depends on four things:
	1. Performance measure of success.
	2. Agent's prior knowledge of environment.
	3. Available actions by the agent.
	4. Agent's percept sequence up to that date.
- **Rational Agents**
	- Do the right thing
	- Every entry in the agent function table is correctly filled
	- Selects options to maximize its performance measure.
	- Rationality ≠ omniscience nor perfection.
## Task Environment
- **P**erformance (measure)
- **E**nvironment
- **A**ctuators
- **S**ensors
- There are many dimensions of task environements
	- Fully observable vs. Partially observable
		- Sensors completely understand their environment at all times.
		- Agent doesn't maintain an internal state.
	- Deterministic vs. Stochastic
		- Next state of environment is completely determined by current state/agent execution.
	- Episodic vs. Sequential
		- Agent's experience divided into epidsodes.
	- Static vs. Dynamic
		- Static environments do not change while the agent thinks.
	- Discrete vs. Continuous
		- Distinction in the state of the environment, time, percepts of agent.
	- Single Agent vs. Multi-agent
		- The agent operates by itself in the environment.
	- Known vs. Unknown
		- Are the laws of physics of the environment known?
## Structure of Agents
- Agents are described by their behaviours.
- Job of an AI is to design an agent program that implements the agent function.
	- It maps percepts to actions.
- All *agent programs* have the same skeleton:
	- Input = Current Percepts
	- Output = Action
	- Program = Manipulates input to make output
- There are four kinds of agent programs.
#### Simple Reflex Agents
- Select action on the basis of only current perceptions.
- Only possible in a small variety of situations.
- Work only if the correct decision can be made solely on the basis of the current percept.
	- The environment must be *fully observable*.
- It may get stuck in an infinite loop, and then must randomize its actions to get out.
![[Pasted image 20250925144717.png]]
#### Model-Based Reflect Agents
- It is rarely possible to determine the state of a partially observable environment.
	- The sensors feed into a box which determines the agent's best guess.
![[Pasted image 20250925144738.png]]
#### Goal-Based Agents
- Agents need goals to know which situations are desirable.
- The big difference in this agent from prior ones is that the **future** is taken into account.
- It is more flexible than prior agents.
- For example if it starts to rain, then the agent can update its knowledge of how effectively its breaks will operate.
	- This shows how it can change its variables.
![[Pasted image 20250925150329.png]]
#### Utility-Based Agents
- Some goals have greater utility than others.
- **Utility Functions** map states onto a real number.
	- The number describes the associated degree of goodness or success.
- The utility measure comes from any variety of sources.
	- Economics --> Money
	- Biology --> Number of Offspring
	- Exam --> Mark
	- Game --> Score or Fun
![[Pasted image 20250925151622.png]]
- A utility agent has advantages in flexibility and learning.
- If goals are inadequate, the agent can still make rational decisions.
## Learning Agents
- All the previous agents describe methods for selecting actions.
	- This does not explain how agent programs come into being.
![[Pasted image 20250925151852.png]]
- Learning agents have four conceptual components:
	1. Learning Element
		- Responsible for making improvements, which are introduced in the *performance element.*
	2. Performance Element
		- Responsible for selecting external actions based on its percepts.
	3. Critic
		- Informs the LE how the agent is doing with respect to a constant/fixed performance standard.
		- Necessary, as the percepts themselves don't provide an indication of the agent's success.
	4. Problem Generator
		- Suggest exploratory actions leading to new experiences.
		- These may be suboptimal in the short run, but lead to the discovery of better long-run actions.
## How Agent Programs Components Work
- Representations of the environment:
	- **Atomic**
		- Each state of the world is indivisible.
		- No internal structure
		- Ex. search, Hidden Markov Models, etc.
	- **Factored**
		- Splits up each state into a fixed set of variables or attributes
		- Each of these variables has a value
		- Ex. Constraint satisfaction, Bayesian Networks, machine learning, etc.
	- **Structured**
		- Structured representations
		- Relationships.
		- Ex. First-order logic models, knowledge-based learning, etc.
		- 