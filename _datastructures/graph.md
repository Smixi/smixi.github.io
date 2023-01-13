---
title: "Adjacency Sets Graph implementation in Python"
collection: datastructures
excerpt: "Creating a Graph in python using Adjacency Sets"
---

## What is a Graph datastructure ?

First, we (or [wikipedia](https://en.wikipedia.org/wiki/Graph_(abstract_data_type))) will define what a graph is:
> In computer science, a graph is an abstract data type that is meant to implement the undirected graph and directed graph concepts from the field of graph theory within mathematics. 
A graph data structure consists of a finite (and possibly mutable) set of vertices (also called nodes or points), together with a set of unordered pairs of these vertices for an undirected graph or a set of ordered pairs for a directed graph. These pairs are known as edges (also called links or lines), and for a directed graph are also known as edges but also sometimes arrows or arcs. The vertices may be part of the graph structure, or may be external entities represented by integer indices or references.

To reformulate: a graph is a list of nodes linked together with edges. A graph can be directed, which means the edges also have a direction (from a certain to another one) or undirected (there is no specific direction for a link). There is also graphs that have specific properties that have their own names and can be used as a specific datastructures, such as Trees.

Graphs are really usefull, they can be used to solve problems or modelize specific domains. For instance, a genealogical tree is graph,Networking in computer science use graph all the time, for example to perform routing tasks. Roads and Airport connections is also a graph that can be directed, and edges can have values (or weighs), for instance the distance between two destinations.

Here is some visuals representations of graphs:
{% include figure image_path="/assets/images/datastructures/graphs/python/graph-visual.svg" alt="a graph representation" caption="A simple Directed graph [(src)](https://en.wikipedia.org/wiki/Directed_graph)" %}{: .align-center}

{% include figure image_path="/assets/images/datastructures/graphs/python/graph-visual2.jpg" alt="a graph representation" caption="Users connected on instagram to a specific profile [(src)](https://www.flickr.com/photos/speedoflife/)" %}{: .align-center}

## Graph Representation

There is two main representation of a graph (and variations):

- Adjacency Matrix
- Adjacency List


### Adjacency Matrix
Let's say we denote nodes from 0 to n-1.
An adjacency matrix is a 2D array where a link between node i and node j is present if the value in the array at position (i, j) is 1. 

They both work for directed and undirected graph, and we can even put specific values instead of 1.

For an undirected graph: 
{% include image.html
max-width="300px" file="/assets/images/datastructures/graphs/python/graph-matrix0.svg" alt="adjacency matrix" %}{: .align-center }
The associated matrix would be: $$\begin{bmatrix}
1 & 5\\
5 & 1
\end{bmatrix}$$
Notice that the matrix will be symetrical.

For a directed graph:

{% include image.html
max-width="300px" file="/assets/images/datastructures/graphs/python/graph-matrix1.svg" alt="adjacency matrix" %}{: .align-center }

The associated matrix would be: $$\begin{bmatrix}
1 & 5\\
0 & 0
\end{bmatrix}$$

### Adjacency List

This representation is used to store all the links of a node.
Let's show another graph and build the adjacency list: 

{% include image.html
max-width="300px" file="/assets/images/datastructures/graphs/python/graph-adj0.svg" alt="Jekyll logo" %}{: .align-center }


We will take each nodes, and for each, get all the links and the associated node. For an undirected graph, a link is added in the adjacency list of both nodes. 

{% include figure image_path="/assets/images/datastructures/graphs/python/graph-adjacency-list.svg" alt="adjacency matrix" %}{: .align-center }

### Adjacency Set

Adjacency set is using the same principle has Adjacency List, storing only links related to each node. This difference is that instead of using a list, we use a mapping. Instead of iterating through each neighbors one by one, we have constant time access by using a map function, like hashing. 

### Why should I use Adjacency Matrix or Adjacency List ?

You may ask yourself, if there is multiple representations, is there one better than the other ?

The answer is yes ... and no ! In fact, It just depends on what type of operations you will perform on the graph. Let's compare their space and time [complexity](https://en.wikipedia.org/wiki/Computational_complexity#Time)). n is for nodes, l for links, v for the number of links of a given node.

|  | Adjacency Matrix | Adjacency List | Adjacency Set |
|---|---|---|---|
| Space Complexity | O(n²) | O(n+l) | O(n+l) |
| Adding link | O(1) | O(1) | O(1) |
| Removing Link | O(1) | O(v) | O(1) |
| Checking if link exists | O(1) | O(v)  | O(1) |
| Iterating throughs neighbors | O(n) | O(v) | O(v) |

Ok, so we can explain how we figured out those complexities and when we can use one or the other.

#### Space Complexity

Obviously, the Matrix will always have an array allocated to store all links between each nodes, so you will have n*n space taken.
For List and Set, we store only nodes and their neighbors: O(n+l). In the case we have fully connected graph (every node are connected), then we go back to the O(n²).

### Python implementation:

All the sources of this implementation are available [here](https://github.com/Smixi/learning-datastructures/blob/main/python/graph/undirected_graph/undirected_graph.py)