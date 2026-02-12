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
- Skinning me