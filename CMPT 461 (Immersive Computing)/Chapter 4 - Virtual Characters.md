## Virtual Humans in Virtual Environments
- **VR**: A technology capable of shifting a subject into a different environment without physically moving him or her
- **Immersion**: User becoming part of the simulated world
- **Presence**: The psychological sense of being in a simulated world
- A virtual world can be inhabited by virtual characters
	- Increase immersion
- **Believability** is important for virtual humans
	- Real behaviours
		- Perception
		- Language understanding
		- Emotions
		- etc.
	- Affected by what takes places around it
	- Engage in social behaviours
	- Conscious and unpredictable
## Character Skinning
- **Rigging**: Constructing a series of bones, which is custom designed to animate characters
- **Skinning**: Process of associating each bone to some portion of the character's visual representation
- There are 3 approaches to skinning:
	1. Skeleton-based
	2. Data-Driven
	3. Physics-based
### Skeleton-Based Deformations
- Other names:
	- Subspace deformation (SSD)
	- Linear Blend skinning
	- Smooth skinning
- Portions of the character's skin
	- Normally associated with multiple bones
	- Skin near the joints of two bones are influenced by both
- Joint-dependent local deformation (JDL)
	- Operators to smoothly deform the skin surface
- Make use of an initial neutral pose
- Fast results, compact memory
- Undesirable deformation artifacts in case of important variation of joint angles among the influencing joints
### Data-Driven Methods
- Overcome the limitation of geometric skin deformation
	- Use examples of various postures and blend them during animation
- For real-time applications
- Efficiently leverage realistic shapes from:
	- Skin shape of real people
	- Physically based simulations
	- Sculpted by skilled designers
- 3D acquisition devices for reliable and accurate data from complex shapes like the human body
- Use real data to cover the space of character shape variation
- Skinning Mesh Animations (SMAs)
	- An original skin example-based scheme
	- No predefined skeleton
	- Automatically estimates statistically relevant bones
### Physics-Based Approaches
- Dynamically-based deformations
- Could be based on a framework for skeleton-driven animation of elastically deformable characters
- Embed the object in a control lattice
- Use continuum elasticity and finite element models (FEM) to compute the dynamics of the object being deformed
- Bones of the control skeleton are restricted to lying along the edges of the control lattice, so that the skeleton can be considered a constraint in the dynamic system.
## Locomotion
- **Locomotion generation**
	- Human Walking
		- Global - Common joint angle variations
		- Specific - Individual walk characteristics are overlaid to the global walking manner (gait)
	- Walking alternates the centre of gravity from right to left.
- **Walking Characteristics**
	- At any time, at least one foot is in contact with the floor
	- There is a short point in which both feet are in contact
	- A periodic motion that has to be normalized in order to adapt to different anatomies
- **Techniques and Approaches**
	- Key-Framing
		- An animator specifies key postures at specific key times using appropriate software
		- Labour-intensive
	- Kinematics
		- Generate motions from parameters such as position, feet, or speed value.
		- Use a predefined set of foot positions and timing information
	- Dynamics
		- Describe a motion by applying physics laws
		- Use control algorithm to describe a particular motion
		- Not easy to determine the influence of each parameter on the resulting motions
	- Motion Capture Data
		- Less work, cost-effective, and rapid results
		- Highly effective
		- Technologically advanced
- **Principal Component Analysis (PCA) Locomotion**
	- PCA is used to compress data or emphasize similarities between input data
	- Generate motion according to control parameters such as age or gender
	- Applied on a motion-capture database composed of various walking and running cycles
	- Generation is performed by interpolation and extrapolation into a hierarchical structure of PCA spaces.
- **Feature Modelling and Smart Objects**
	- Virtual human manipulated objects have two issues:
		1. Specification of object behaviour
		2. Valid and believable motion for humans/objects
	- **Grasping**
		- The human hand is a very complicated structure
		- Need to calculate the hands join movement and arm reaching movements
		- 