## Graph Nomenclature
- Similarly to trees, *graphs* are made up of nodes, and the connection between those nodes.
- On graphs, we refer to nodes as *vertices* and refer to connections as *edges*.
- Vertices are typically referred to with a name.
- An *undirected graph* is a graph where the pairings representing the edges are unodered.
- A graph G = (V,E) is composed of:
	- V: set of *vertices*
	- E: set of *edges* connecting the *vertices* in V.

![[Pasted image 20241128152327.png]]

- A graph G is an ordered pair (V,E) consisting of the vertex set (V) and edge set (E)

###### Graph Applications
- Electronic circuits.
- Networks (roads/flights/communications).
- Visibility problems.
## Undirected Graphs
- An edge in an undirected graph may be traversed in either direction.
- **Adjacent/Neighbours**: Two vertices when there is an edge connecting them.
- **Self Loop/Sling**: An edge of a graph that connects to itself.
- **Complete**: It has the maximum number of edges connecting vertices.
- **Simple Graph**: A graph with no loops nor multiple edges.
- **Path**: A sequence of edges that connects two vertices in a graph.
	- **Simple**: Each vertex is distinct.
	- **Circuit**: A path wherein the terminal vertex coincides with the initial vertex.
	- **Length**: The # of edges in the path (or the # of vertices minus 1).
	- **Cycle**: A path in which the first and last vertices are the same, and none of the edges are repeated.
- **Connected**:  For any two vertices in the graph, there is a path between them.
## Directed Graphs
- **Directed Graph/Digraph**: The edges of the graph are ordered pairs of vertices.
	- Therefore, edges (A,B) and (B,A) are separate, directional edges.
	- If there are n vertices, then there are n(n-1) edges.
- Example below:
	- Vertices A, B, C, D.
	- Edges(A,B), (A,D), (B,C), (B,D) and (D,C).
![[Pasted image 20241128154353.png]]



