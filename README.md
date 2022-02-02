# SLI-Node-Importance-Measure
This is the Python implementation of the Semi-Local Intregation (SLI) measure, a node centrality measure for undirected and weighted graphs that takes into account the coherence of the locally connected subnetwork and evaluates the integration of nodes within their neighbourhood. The method has been described in the paper Ban Kirigin, Tajana, Sanda Bujačić Babić, and Benedikt Perak. 2022. "Semi-Local Integration Measure of Node Importance" Mathematics 10, no. 3: 405. https://doi.org/10.3390/math10030405

Abstract: https://www.mdpi.com/2227-7390/10/3/405

PDF Version: https://www.mdpi.com/2227-7390/10/3/405/pdf

# Example of usage
## Construct a graph G
```
import networkx as nx
from matplotlib import pyplot as plt

# construct an example graph G
G = nx.Graph()

cycles = [[1, 2, 4], [1, 3, 4], [1, 5, 6], [3, 4, 40], [5, 6, 52]]
for cycle in cycles:
  nx.add_cycle(G, cycle)
cycles = [[1, 2, 4], [1, 3, 4], [1, 5, 6], [3, 4, 40], [5, 6, 52]]
for cycle in cycles:
  nx.add_cycle(G, cycle)

edges_tuple = [(1, 2, 3),(1, 3, 1.75),(1, 4, 3),(1, 5, 2),(1, 6, 2.5),(1, 7, 0.4),(2, 4, 0.4),(2, 20, 0.8),(2, 21, 2),(2, 22, 0.7),(2, 23, 1),(2, 60, 1.5),(3, 4, 1.4),(3, 40, 0.5),(3, 30, 0.6),(3, 31, 1),(3, 32, 0.4),(4, 40, 1.5),(4, 41, 0.75),(4, 42, 0.4),(5, 6, 1.5),(5, 50, 0.4),(5, 51, 0.8),(5, 52, 1),(6, 52, 0.4),(6, 60, 1.2),(6, 61, 0.5),(7, 70, 2),(7, 71, 0.8),(7, 72, 0.4)]
for edge in edges_tuple:
    G.add_edge(edge[0], edge[1], weight=edge[2])

# Set weighted_degree attribute on nodes
weights = nx.get_edge_attributes(G,'weight').values()
weighted_degree =  dict((x,y) for x,y in (G.degree(weight='weight')))
nx.set_node_attributes(G, weighted_degree, "weighted_degree")
```
## Calculate sli_importance for nodes in the graph G
```
# import sli_importance method from sli.py
from sli import sli_importance
sli_importance(G, igraph=False, normalize=True).tolist()
```
## SLI Example output normalized
```
[40.224704875135764, 16.22542192814501, 13.269411294301452, 6.663528746817569, 6.9607760164571, 9.614365991921142, 0.9691339164377623, 0.5457920575714295, 1.2384765902759793, 0.1657253650287946, 0.5686404349795474, 0.1388144950602838, 0.22363296026280205, 1.6706620823076415, 0.11021241324706493, 0.21021712918000718, 0.06666126151529841, 0.14964230679754376, 0.06726142386351164, 0.06668271540616122, 0.1586556899362313, 0.0880978328308008, 0.3888086725541725, 0.14935394297783425, 0.06531985698910099]
```
## Graph G
```
../blob/main/pic_graphSLI.pdf

```
## Citation
```
If you use the introduced Semi-Local Integration Measure, we kindly ask you to cite our article "Semi-Local Integration Measure of Node Importance", published in Mathematics as part of the Special Issue New Trends in Graph and Complexity Based Data Analysis and Processing:

Ban Kirigin, Tajana, Sanda Bujačić Babić, and Benedikt Perak. 2022. "Semi-Local Integration Measure of Node Importance" Mathematics 10, no. 3: 405. https://doi.org/10.3390/math10030405

Abstract: https://www.mdpi.com/2227-7390/10/3/405

PDF Version: https://www.mdpi.com/2227-7390/10/3/405/pdf

You can find the uploaded BibTeX file with all necessary information in our main branch.

