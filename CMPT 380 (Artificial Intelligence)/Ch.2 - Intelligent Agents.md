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
	- It 