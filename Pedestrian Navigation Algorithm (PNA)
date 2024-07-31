<h2>Pedestrian Navigation Algorithm (PNA) Based on Sidewalk Context Data</h2>

__Phase I: The K-Shortest Paths Calculation__ <br>
The algorithm finds the k-shortest paths between A and B. The general idea is to find the shortest path, then progressively find paths with increasing weight that are not dominated by already found paths.

__1. Graph Representation__ <br>
<ul>
 <li>G = (V, E): A directed graph with a set of vertices V and a set of edges E.</li>
 <li>w(u, v): The weight (or cost) associated with the edge (u, v) ∈ E.</li>
</ul>

__2.	Problem Definition__ <br>
Given:
<ul>
 <li>Graph G = (V, E) with edge weights w(u, v)</li>
 <li>Source vertex s ∈ V</li>
 <li>Destination vertex t ∈ V</li>
 <li>Integer k > 0</li>
</ul>
Find:
KSP(s, t, k) = {p1, p2, ..., pk}: A set containing the k-shortest paths from s to t in G, ordered by increasing path weight. <br><br>

d(p): The weight of a path p = (s, v1, v2, ..., t) is defined as the sum of the edge weights: <br>
d(p) = ∑ w(vi, vi+1), for 0 ≤ i ≤ |p|-2, where v0 = s and v|p|-1 = t

__3.	General Algorithm__ <br>
<ul>
 <li>Initialization:</li>
 <ul>
  <li>Find the shortest path p1 from s to t using Dijkstra's algorithm.</li>
  <li>Set KSP(s, t, k) = {p1}</li>
  <li>Set i = 1</li>
 </ul>
<li>Iteration:</li>
  For i = 1 to k-1:
 <ul>
    <li>Find candidate paths: Generate candidate paths by considering each edge e in the current shortest path pi. For each edge e = (u, v), create a new path by removing e and finding the shortest path from v to t that doesn't use any edges from the previous paths (p1, p2, ..., pi).</li>
    <li>Filter candidates: Remove candidate paths that are dominated by paths already in KSP(s, t, k).</li>
    <li>Select next shortest: Choose the candidate path with the smallest weight that is not dominated and add it to KSP(s, t, k) as pi+1.</li>
 </ul>
    </ul>

__4.	Mathematical Expressions__ <br>
<ul>
 <li>Dominance: A path p' is dominated by path p if it has the same starting and ending nodes, but p' has a higher weight and also contains all the edges of p.</li>
 <li>Candidate Path Generation:</li>
  For each edge e = (u, v) in path pi:
 <ul>
    <li> Let sp = pi - e (the spur path without e) </li>
    <li> Let p' = shortest path from v to t, excluding edges in (p1, p2, ..., pi).</li>
    <li>Candidate path p = sp + p'</li>
 </ul>
<li> Filtering: Remove candidate paths where a path p exists in KSP(s, t, k) such that d(p) ≤ d(p') and p contains all the edges of p'. </li>
</ul>

__5.	Example__ <br>
Consider a graph with nodes A, B, C, D, and edges:
<ul>
<li>AB: weight 1</li>
<li>AC: weight 2</li>
<li>BC: weight 1</li>
<li>BD: weight 2</li>
<li>CD: weight 1</li>
</ul>

Let s = A, t = D, and k = 3. <br>
<ol>
<li>Shortest Path: p1 = AB, BD (weight 3)</li>
<li>Candidate Paths:</li>
 <ul>
  <li>Remove AB: p2 = AC, CD (weight 3)</li>
  <li>Remove BD: p3 = AB, BC, CD (weight 4)</li>
  </ul>
<li>Filtering: None</li>
<li>Next Shortest: p2 is chosen since its weight is equal to p1's but it's not dominated.</li>
<li>Candidate Paths (second iteration):</li>
 <ul>
  <li>Remove AC: p4 = AB, BC, CD (already found)</li>
  <li>Remove CD: p5 = AC, BD (weight 4)</li>
  </ul>
<li>Filtering: None</li>
<li>Next Shortest: p5 is chosen since it's not dominated and its weight is greater than p2's.</li>
 </ol>
 
Therefore, KSP(A, D, 3) = {AB, BD, AC, CD, AC, BD}.
<br>

__Phase II: Attributes Retrieval and Presentation__ <br>
The stored navigation information (e.g., presence of sidewalk, greenery, missing curb ramps, etc.) corresponding to each segment in the “shortest” and “alternative” paths are retrieved from the tables as key-value pairs. Finally, the geometry of the “shortest” and “alternative” paths and their comprehensive sidewalk attributes are presented to the users.
