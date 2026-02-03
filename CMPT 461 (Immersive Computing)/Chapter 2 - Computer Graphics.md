## 3D Modelling
- Drawing with 3D graphics on a computer screen
- Geometric representations are ways to describe the arrangement of 3D vertices to create 3D shapes
- 3 Basic Primitives:
	- **Points**: The simplest primitives
	- **Curves**: Approximated by lines or points
		- Powerful geometric representations
		- Use to describe complex 3D surfaces
	- **Polygons**: Used by graphics cards to approximate any 3D surface
### Triangles
- Simples polygon
- Most efficient for rendering
- More triangles used, more accurate the surface
### Tessellation
- A **tessellation** is a pattern made by repeating shapes that fit together
- They utilize:
	- Regular polygons
		- Triangles, squares, hexagons
	- Transformations
		- Translation, rotation, reflection
- In CS, *tessellation* is the process of subdividing a surface into a mesh of polygons
	- Tessellation ≈ Triangle Subdivision
- *Vertex Set* = A dataset of polygons which divide a scene into renderable structures
### Curves
- Represented by a list of points
	- Connected with short line segments
	- Interpolation = loose drawing precision
	- Storage issues and limited resolution
	- Problems with computation and transformation
- Represented by analytical definition
	- Precise
	- Compact storage
	- Easy calculation of intermediate points
- **Interpolation**: Calculation of the value of a function between the already known values
#### Nonparametric Curves
- Explicit: y = f(x) --> Straight lines
- Implicit: f(x,y) = 0 --> curves/circles
- Limitations:
	- Axis-dependent
		- Choice of coordinate system affects ease of use
	- Unequal point distribution
		- Affects the quality and accuracy of the visual
### Parametric Curves
- Each point's coordinates in a curve are represented as functions of a single parameter that varies across a predefined range of values

- How do we represent curves in computer graphics?
	- 
- What are the advantages of using parametric curves over non-parametric curves?
	- Axis independent
	- Normalize the parameter t between 0 and 1
	- Can apply transformations
- What is the difference between local and global illumination?
	- 
- What are the three different reflections in the local illumination model?
	- Ambient
		- Background illumination of unlit surfaces
	- Diffused
		- Dull, matte surfaces
		- Equal intensity from all directions
	- Specular
		- Shiny surfaces
		- Bright highlights from certain directions




















https://learn.twu.ca/pluginfile.php/1692258/mod_resource/content/1/Chapter%202%28Part2%29.pdf