Dijkstra’s algorithm

```bash
Dijkstra(Graph, source):
    Initialize distances:
        For each vertex v in Graph:
            v.d = ∞         # Set all distances to infinity
            v.π = NIL       # Set all predecessors to NIL
        source.d = 0         # Distance to source is 0

    Create a priority queue Q containing all vertices in Graph
    
    While Q is not empty:
        u = EXTRACT-MIN(Q)  # Get vertex with smallest distance estimate
        For each neighbor v of u:
            If v is still in Q:  # Only consider unvisited vertices
                Relax(u, v, Graph)

    Return distances and predecessors

Relax(u, v, Graph):
    If v.d > u.d + ω(u, v):    # Check if a shorter path is found
        v.d = u.d + ω(u, v)    # Update distance to v
        v.π = u                # Update predecessor of v

```

```bash
Dijkstra(Graph G, Vertex s):
    INITIALIZE-SINGLE-SOURCE(G, s)   # Set initial distances and predecessors
    S = ∅                           # S is the set of vertices with final shortest paths
    Q = G.V                         # Q is the priority queue of all vertices

    While Q is not empty:
        u = EXTRACT-MIN(Q)          # Get the vertex with the smallest distance estimate
        Add u to S                  # Mark u as "done"

        For each vertex v in G.Adj[u]:   # Explore all neighbors of u
            RELAX(u, v, G)

    Return distance and predecessor arrays

INITIALIZE-SINGLE-SOURCE(Graph G, Vertex s):
    For each vertex v in G.V:
        v.d = ∞                     # Set initial distances to infinity
        v.π = NIL                   # No predecessors initially
    s.d = 0                         # Source has a distance of 0

RELAX(Vertex u, Vertex v, Graph G):
    If v.d > u.d + ω(u, v):         # Check if we can improve v's shortest-path estimate
        v.d = u.d + ω(u, v)         # Update v's distance
        v.π = u                     # Set u as v's predecessor

```