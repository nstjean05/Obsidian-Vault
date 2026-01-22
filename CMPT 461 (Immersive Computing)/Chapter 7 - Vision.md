## Human Vision
- Primary source of information about the outside world
- Not always the most relevant, but often used to double check other senses accuracy
- **Stereo Vision** is the main source of depth perception
	- Slight difference in the angle of the two eyes in what they see
- **Monocular Cues** allow one eye to see some depth
	- Light/shade
	- Relative Size
	- Overlap
	- etc.
## Virtual Visual System
- There are several factors for a sense of visual immersion
	- FOV
	- Refresh rate
	- Stereopsis: ability to perceive the world in 3D
	- Resolution
## Graphical Display Technologies
#### Cathode-Ray Tubes (CRTs):
- Invented by Karl Ferdinand in 1879
- Coils use magnetism to deflect the ray of electrons to a point of phosphor, which displays on the screen
#### Liquid Crystal Displays (LCDs):
- Discovered by Friedrich Reinitzer in 1888
- Uses liquid crystal, which twists to let pass through, or untwists to block it.
- Six layers:
	1. Vertical polarizing film
	2. Glass substrate with ITO electrodes (determines shape when LCD is on)
	3. Twisted nematic liquid crystal
	4. Glass substrate with common electrode film (horizontal ridges to align with horizontal filter)
	5. Horizontal polarizing film
	6. Reflective surface to send light to viewer
		- Backlit lCDs replace this with a light source
- Two types of LCDS:
	- Passive-Matrix
		- Simple grid of two glass layers (row/col), with liquid crystal between them
		- Charge sent to a particular col/row to turn on a pixel
		- Slow and imprecise voltage control
	- Active-Matrix
		- Thin film transistors (TFTs) are arranged in a matrix on the glass
		- Only the proper row and column are switched on
		- Amount of voltage is proportional to light passing through
		- Colour LCDs have 3 sub-pixels (RGB)
#### Plasma Displays
- Invented in 1964 at University of Illinois
- Flat display with many cells between two glass panels, containing inert gases
	- Electrically turned in a plasma (UV) to emit light
- Wide screen, high brightness, fast response, wide view
- Screen burn-in, more power
#### Digital Light Processing (DLP)
- Uses micro-mirrors to reflect light onto a larger surface
- Mostly used in projectors
#### Liquid Crystal on Silicon (LCoS)
- High resolution micro-displays for projectors or VR
- High pixel density, contrast, and detail
#### Organic Light-Emitting Diode (OLED)
- An LED display wherein the electroluminescent layer of film emits light in response to electric current.
- Allows for 'perfect blacks'
	- Each pixel has its own light source, rather than a backlight layer
#### Active-Matrix Organic Light-Emitting Diode (AMOLED)
- Adds the TFT technology from LCDs on top of an OLED display for even more control.
- Faster response time, brighter, power efficiency, smoother visuals
- Still susceptible to burn-in
## VR Displays
- Have two main categories; **individual** or **collective**
- Classified on the degree of visual immersion
- Range from HMDs to handheld displays
#### Head-Mounted Displays (HMDs)
- One or two small displays
- CRT, LCD, LCoS, or OLED
- Include sound equipment and a tracking device
- Stereoscopic images for two displays
- FOV from 110° horiz/96°vert, and 3 or 6 degrees of freedom (DoF)
- Can be wired or wireless
- **See-Through HMDs**
	- A CG image superimposed on the real world
	- Project a synthetic image on a semitransparent mirror
- Advantages: Most immersive experience, appropriate for VR applications with frequent turns/spatial orientation
- Disadvantages: Motion sickness
#### Fish Tank VR
- Use a high-res monitor with hardware for stereoscopic viewing
- LCD shutter glasses alternately cover one eye and show an image to the other, producing a stereoscopic effect.
#### Large Projection Screens
- Semi-immersive
- Stereo glasses and 3D surround sound can enhance the effect
- Allow direction interaction/communication between users
#### CAVE Systems
- Designed in 1992
- CAVE Automatic Virtual Environment
- Ideally overcomes poor resolution and inability to share experience with others, and isolation from reality
- Head tracking allows for a correct stereo perspective
- Disadvantages: Expensive, still in prototypes, and very specific care/maintenance
## Summary

|Display Type|Advantages|Disadvantages|
|---|---|---|
|**Human Vision**|Primary source of info, stereo vision for depth, monocular cues for single-eye depth perception|Subjective, can be misleading, limited by biological constraints|
|**Cathode-Ray Tubes (CRTs)**|High refresh rates, good color accuracy, low input lag|Bulky, heavy, high power consumption, screen flicker|
|**Liquid Crystal Displays (LCDs)**|Thin, lightweight, energy efficient, no screen burn-in (usually)|Limited viewing angles, slower response time (passive-matrix), backlight bleed|
|**Plasma Displays**|Wide screen, high brightness, fast response, wide viewing angles|Screen burn-in, higher power consumption, heavier than LCDs|
|**Digital Light Processing (DLP)**|High contrast, smooth motion, good for large venues/projectors|Rainbow effect (color separation), bulb replacement needed, limited viewing angles|
|**Liquid Crystal on Silicon (LCoS)**|High resolution, high pixel density, good for VR/projectors|Expensive, complex manufacturing, limited brightness|
|**Organic Light-Emitting Diode (OLED)**|Perfect blacks, thin, lightweight, flexible, wide viewing angles|Screen burn-in, shorter lifespan, expensive|
|**Active-Matrix OLED (AMOLED)**|Faster response, brighter, power efficient, smoother visuals|Screen burn-in, expensive, complex manufacturing|
|**Head-Mounted Displays (HMDs)**|Most immersive, high FOV, stereoscopic 3D, suitable for VR applications|Motion sickness, can be heavy/bulky, expensive, potential isolation|
|**Fish Tank VR**|High resolution, stereoscopic effect, less motion sickness|Limited FOV, requires shutter glasses, less immersive than HMDs|
|**Large Projection Screens**|Semi-immersive, shared experience, good for group interaction|Requires space, lower resolution per user, limited portability|
|**CAVE Systems**|Shared immersive experience, head tracking for correct perspective, high immersion|Expensive, prototype stage, high maintenance, space-intensive|