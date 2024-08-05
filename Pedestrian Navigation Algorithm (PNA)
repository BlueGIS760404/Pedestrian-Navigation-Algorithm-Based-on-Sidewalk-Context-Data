<h2>Pedestrian Navigation Algorithm (PNA) Based on Sidewalk Context Data</h2>

__Phase I: The K Shortest Paths Calculation__ <br>
Yen's algorithm is used to find the k shortest paths between a source and a destination. It uses Dijkstra's shortest path algorithm to calculate the shortest paths between two nodes in a graph network. Dijkstra's algorithm is a graph-based greedy search technique that finds the shortest path between a start node and all other nodes in a graph. The Yen's algorithm ensures that a previously discovered shortest path is not traversed again. The algorithm has a worst-case complexity of O(kNA+NlogN), where \(k\) is the number of shortest paths, \(N\) is the number of nodes in the road network, and \(A\) is the number of links in the road network.

<ol>
 <li>
  
__Graph Representation__ </li>
<ul>
 <li>G = (V, E): A directed graph with a set of vertices V and a set of edges E.</li>
 <li>w(u, v): Weight of edge (u, v) ∈ E, representing distance, time, or any other relevant metric.</li>
 <li>s: Source vertex.</li>
 <li>t: Destination vertex.</li>
 <li>k: Number of shortest paths to be found (k > 0).</li>
 <li>P(s, t): Set of all possible paths from s to t.</li>
 <li>d(p): Total weight of path p, sum of weights of all edges in the path.</li>
 <li>KSP(s, t, k): Set of k shortest paths from s to t, ordered by increasing path weight.</li>
 <li>SP(s, t): Shortest path from s to t.</li>
</ul>

<li>
 
__Problem Definition__ </li>
Given:
<ul>
 <li>Graph G = (V, E) with edge weights w(u, v)</li>
 <li>Source vertex s ∈ V</li>
 <li>Destination vertex t ∈ V</li>
 <li>Integer k > 0</li>
</ul><br>

Find:<br>
KSP(s, t, k) = {p1, p2, ..., pk}: A set containing the k-shortest paths from s to t in G, ordered by increasing path weight.

<li>
 
__Path Weight__ </li>
d(p): The weight of a path p = (s, v1, v2, ..., t) is defined as the sum of the edge weights: <br>
d(p) = ∑ w(vi, vi+1), for 0 ≤ i ≤ |p|-2, where v0 = s and v|p|-1 = t

<li>
 
__General Algorithm__ </li>
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

<li>
 
__Mathematical Expressions__ </li>
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

<li>
 
__Example__ </li>
Consider a graph with nodes A, B, C, D, and edges:
<ul>
<li>AB: weight 1</li>
<li>AC: weight 2</li>
<li>BC: weight 1</li>
<li>BD: weight 2</li>
<li>CD: weight 1</li>
</ul><br>

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
 </ol><br>
 
Therefore, KSP(A, D, 3) = {AB, BD, AC, CD, AC, BD}.
<br>
</ol>

__Phase II: Attributes Retrieval and Presentation__ <br>
The stored navigation information (e.g., presence of sidewalk, greenery, missing curb ramps, etc.) corresponding to each segment in the “shortest” and “alternative” paths are retrieved from the tables as key-value pairs. Finally, the geometry of the “shortest” and “alternative” paths and their comprehensive sidewalk attributes are presented to the users.
<ol>
<li>Initialize empty dictionaries to store the edge's attributes of each path as key-value pairs.</li>
<li>Until all the calculated paths have been explored:</li>
 <ul>
 <li>For each edge in path:</li>
  <ul>
   <li>Extract all the edge's attributes and add them to the corresponding dictionary.</li>
  </ul>
  </ul>
 <li>For each key of edge's attributes:</li>
 <ul>
  <li>Extract unique values and sum of the related length.</li>
  <li>Return % of path that is of type unique value.</li>
 </ul>
 <li>Present the geometry and edge's attributes related to the "shortest" and "alternative" paths.</li>
</ol>
