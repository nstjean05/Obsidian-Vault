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
	- 