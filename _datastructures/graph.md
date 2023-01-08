---
title: "Simple graphs implementation in Python."
collection: datastructures
---

## What is a Graph datastructure ?

First, we (or [wikipedia](https://en.wikipedia.org/wiki/Graph_(abstract_data_type))) will define what a graph is:
> In computer science, a graph is an abstract data type that is meant to implement the undirected graph and directed graph concepts from the field of graph theory within mathematics. 
A graph data structure consists of a finite (and possibly mutable) set of vertices (also called nodes or points), together with a set of unordered pairs of these vertices for an undirected graph or a set of ordered pairs for a directed graph. These pairs are known as edges (also called links or lines), and for a directed graph are also known as edges but also sometimes arrows or arcs. The vertices may be part of the graph structure, or may be external entities represented by integer indices or references.

To reformulate: a graph is a list of nodes linked together with edges. A graph can be directed, which means the edges also have a direction (from a certain to another one) or undirected (there is no specific direction for a link). There is also graphs that have specific properties that have their own names and can be used as a specific datastructures, such as Trees.

Graphs are really usefull, they can be used to solve problems or modelize specific domains. For instance, a genealogical tree is graph,Networking in computer science use graph all the time, for example to perform routing tasks. Roads and Airport connections is also a graph that can be directed, and edges can have values (or weighs), for instance the distance between two destinations.

Here is some visuals representations of graphs:
{% include figure image_path="/assets/images/datastructures/graphs/python/graph-visual.svg" alt="a graph representation" caption="A simple Directed graph [src](https://en.wikipedia.org/wiki/Directed_graph)" %}

{% include figure image_path="/assets/images/datastructures/graphs/python/graph-visual2.jpg" alt="a graph representation" caption="Users connected on instagram to a specific profile [src](https://www.flickr.com/photos/speedoflife/)" %}

## Python implementation

All the sources of this implementation are available here: 