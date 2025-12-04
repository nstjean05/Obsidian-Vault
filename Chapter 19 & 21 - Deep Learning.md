# Agents We Have Learned
### Problem Solving Agents
- Systematic search
	- Uninformed or informed
- Local Search
- Adversarial Search
### Logical Agents
- Knowledge-based agents
- Propositional Logic
- First-order logic
### Probabilistic Agents
- Quantifying Uncertainty
- Probabilistic Reasoning
# Training
- **Question: How Do We Learn?**
	- Learning problems involve classifying inputs into classifications.
	- Learning is possible only if there is a relationship between data and classifications.
	- Relationships are based on similarity.
	- **Training** --> Providing the system with manually classified data.
	- Learning systems use training data to learn to classify unseen data.
# Intelligence
- This is the capacity to learn and solve problems.
- Act rationally and reason.
# Learning Agents
- Remember the 5 aspects discussed earlier:
	1. **Learning Element**
		- Adds knowledge and make system improvements
	2. **Performance Element**
		- Perform the task and choose external actions
	3. **Critic**
		- Monitor the performance results and provide feedback
	4. **Problem Generator**
		- Actively suggest experiments and generate examples
	5. **Performance Standard**
		- Method and standard performance measures.
- An autonomous agent must learn how to use probabilities and rules on its known, and this is accomplished by machine learning.
### What is Learning?
- Machine learning refers to a system capable of the autonomous acquisition and integration of knowledge.
- If a system is capable of learning, its is generally considered intelligent.
### Forms of Learning
- There are four major techniques to make improvements to learning data:
	1. The **component** to be improved
	2. The agent's **prior knowledge**
	3. The data's **representation**
	4. What **feedback** is available to learn from.
- Chapter 2's agent's had various components:
	1. Direct mapping from the current state's conditions to actions
	2. Infer relevant details about environment from percepts
	3. Take information about the worlds evolution to determine results of actions.
	4. Utility info indicating state desirability
	5. Action-value info indicating action desirability
	6. Goals describing state classes whose achievement maximizes agent utility.
- These components can all be learned.
- Machine learning takes **factored representations** of inputs (vectors)
	- Outputs a continuous numerical value or a discrete value
- **Inductive**
	- Learns specific examples, and discover applicable rules.
- **Deductive**
	- Learns a general rule (or set), and applies this to situations.
- Most machine learning models use a specific type of one of these models.
	- A model is made up of these general rules.
	- 