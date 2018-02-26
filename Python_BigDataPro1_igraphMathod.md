# igraph Methods

##1. Read_Edgelist(f, directed=True)
Reads and edge list from a file and creates a graph based on it.

Please note that the vertex indices are zero-based.

	parameter:
	f - the name of the file or a Python file handle
	directed - whether the generated graph should be directed
 
##2. average\_path\_length(directed=True, unconn=True)
Calculates the average path length in a graph.

	parameter:
	directed - whether to consider directed path in case of a directed graph. Ignored for undirected graphs.
	unconn - what to do when the graph is unconnected. If True, the average of the geodesic lengths in the components is calculated. Otherwise for all unconnected vertex pairs, a path length equal to the number of vertices is used.
	return the average path length in the graph
	
##3. betweenness(vertices=None, directed=True, cutoff=None, weights=None, nobigint=True)
Calculates or estimates the betweenness of vertices in a graph.
	
	parameter:
	vertices - the vertices for which the betweennesses must be returned. If None, assumes all the vertices in the graph.
	directed - whether to consider directed paths.
	cutoff - if it is an integer, only paths less than or equal to this length are considered,effectively resulting in an estimation of the betweenness for the given vertices. If None, the exact betweenness is returned.
	weights - edge weights to be uesd. Can be a sequence or iterable or even an edge attribute name.
	nobigint - if True, igraph uses the longest available integer type on the current platform to count shortest paths. For some large networks that have a specific structure, the counters may overflow. To prevent this, use nobigint=False, which forces igraph to use arbitrary precision integers at the expense of increased computation time.
	return the (possibly estimated) betweenness of the given vertices in a list.
	
##4. clique_number()
Returns the clique number of the graph.

The clique number of the graph is the size of the largest clique.

##5. cliques(min=0, max=0)
Returns some or all cliques of the graph as a list of tuples.

A clique is complete subgraph -- a set of vertices where an edge is present between any two of them (excluding loops)
	
	parameters:
	min - the minimum size of cliques to be returned. If zero or negative, no lower bound will be used.
	max - the maximum size of cliques to be returned. If zero or negative, no upper bound will be used.
	
##6. largest_cliques()
Returns the largest cliques of the graph as a list of tuples.

Quite intuitively a clique is considiered largest if there is no clique with more vertices in the whole graph. All largest cliques are maximal (i.e. nonextendable) but not all maximal cliques are largest.

##7. maximal_cliques(min=0, max=0)
Return the maximal cliaues of the graph as a list of tuples.

A maximal clique is a clique which can't be extended by adding any other vertex to it. A maximal clique is not necessarily one of the largest cliques in the graph.

	parameters:
	min - the minimum size of maximal cliques to be returned. If zero or negative, no lower bound will be used.
	max - the maximum size of maximal cliques to be returned. If zero or negative, no upper bound will be uesd. If nonzero, the size of every maximal clique found will be compared to this value and a clique will be returned only if its size is smaller than this limit.

##8. closeness(vertices=None, mode=All, cutoff=None, weights=None, normalized=True)
Calculates the closeness centralities of given vertices in a graph.

The closeness centerality of a vertex measures how easily other vertices can be reached from it (or the other way: how easily it can be reached from the other vertices). It is defined as the number of the number of vertices minus one divided by the sum of the lengths of geodesics from/to the given vertiex.

If the graph is not connected, and there is no path between two vertices, the number of vertices is uesd instead the length of the geodesic. This is always longer than the longest possible geodesic.

	parameters:
	vertices - the vertices for which the closenesses must be returned. If None, uses all of the vertices in the graph.
	mode - must be one of IN, OUT and ALL. IN means that the length of incoming paths, OUT means that the length of the outgoing paths must be calculated. ALL means that both of that both of them must be calculated.
	cutoff - if it is an integer, only paths less than or equal to this length are considered, effectively resulting in an estimation of the closeness for the given vertices (which is always an underestimation of the real closeness, since some vertex pairs will appear as disconnected even though they are connected). If None, the exact closeness is returned.
	weights - edge weights to be used. Can be a sequence or iterable or even an edge attribute name.
	normalized - whether to normalize the raw closeness scores by multiplying by the number of vertices minus one.
	return the calculated closenesses in a list.
	
##9. coreness(mode=ALL)
Finds the coreness (shell index) of the vertices of the network.

The k-core of a graph is a maximal subgraph in which each vertex has at least degree k. (Degree here means the degree in the subgraph of course). The coreness of a vertex is k if it is a member of the k-core but not a member of the k+1-core,

	parameters:
	mode - whether to compute the in-corenesses(IN), the out-corenesses (OUT) or the undirected corenesses (ALL). Ignored and assumed to be ALL for undirected graphs. 
	return the corenesses for each vertex.
	
##10. diameter(directed=True, unconn=True, weights=None)
Calculates the diameter of the graph.

	parameters:
	directed - whether to consider directed paths.
	unconn - if True and the graph is unconnected, the longest geodesic within a component will be returned. If False and the graph is unconnected, the result is the number of vertices if there are no weights or infinity if there are weights.
	weights - edge weights to be used. Can be a sequence or iterable or even an edge attribute name.
	returns the diameter
	
##11. ecount()
Count the number of edges.

	return the number of edges in the graph.

##12. edge_betweenness(directed=True, cutoff=None, weights=None)
Calculates or estimates the edge betweennesses in a graph.

	parameters:
	directed - whether to consider directed paths.
	cutoff - if it is an integer, only paths less than or equal to this length are considered, effectively resulting in an estimation of the betweenness values. If None, the exact betweennesses are returned.
	weights - edge weights to be used. Can be a sequence or iterable or even an edge attribute name.
	return a list with the (exact or estimated) edge betweennesses of all edges.
	
##13. betweenness(vertices=None, directed=True, cutoff=None, weights=None, nobigint=True, nobigint=True)
Calculates or estimates the betweenness of vertices in a graph.

Keyword arguments:

	parameters:
	vertices - the vertices for which the betweennesses must be returned. If None, assumes all of the vertices in the graph.
	directed - whether to consider directed paths.
	cutoff - if it is an integer, only paths less than or equal to this length are considered, effectively reaulting in an estimation of the betweenness for the given vertices. If None, the exact betweenness is returned.
	weights - edge weights to be used. Can be a sequence or iterable or even an edge attribute name.
	nobigint - if True, igraph uses the longest available integer type on the current platform to count shortest paths. For some large networks that have a specific structure, the counters may overflow. To prevent this, use nobigint=False, which forces igraph to use arbitrary precision integers at expense of increased computation time.
	returns the (possibly estimated) betweenness of the given vertices in a list.
	
##14. get_diameter(directed=True, unconn=True, weights=None)
Returns a path with the actual diameter of the graph.

If there are many shortest paths with the length of the diameter, it returns the first one it founds.

	parameters:
	directed - whether to consider directed paths.
	unconn - if True and the graph is unconnected, the longest geodesic within a component will be returned. If False and the graph is unconnected, the result is the number of vertices if there are no weights or infinity if there are weights.
	weights - edge weights to be used. Can be a sequence or iterable or even an edge attribute name.
	return the vertices in the path in order.
	
##15. simplify(multiple=True, loops=True, combine_edges=None)
Simplifies a graph by removing self-loops and/or multiple edges.

For example, suppose you have a graph with an edge attribute named weight.

graph.simplify(combine_edges=max) will take the maximum of the weights of multiple edges and assign that weight to the collapsed edge.

graph.simplify(combine_edges=sum) will take the sum of the weights. You can also write graph.simplify(combine_edges=dict(weight="sum")) or graph.simplify(combine_edges=dict(weight=sum)), since sum is recognised both as a Python built-in function and as a string constant.

	parameters:
	multiple - whether to remove multiple edges.
	loops - whether to remove loops.
	combine_edges - specifies how to combine the attributes of multiple edges between the same pair of vertices into a single attribute. If it is None, only one of the edges will be kept and all the attributes will be lost. If it is a funtion, the attributes of multiple edegs be collected and passed on to that functoin which will return the new attribute value that has to be assigned to the single collapsed edge. It can also be one of the following string constants:
	'ignore': all the edge attributes will be ignored.
	'sum': the sum of the edge attribute values will be used for the new edge.
	'product': the product of the edge attribute values will be used for the new edge.
	'mean': the mean of the edge attribute values will be used for the new edge.
	'median': the median of the edge attribute values will be used for the new edge.
	'min': the minimum of the edge attribute values will be used for the new edge.
	'max': the maximum of the edge attribute values will be used for the new edge.
	'first': the attribute value of the first edge in the collapsed set will be used for the new edge.
	'last': the attribute value of the last edge in ithe collapsed set will be used for the new edge.
	'random': a randomly selectd value will be used for the new edge.
	'concat': the attribute values will be concatenated for the new edge.
You can also use a dict mapping edge attribute names to functions or the above string constants if you want to make the behaviour of the simplification process depend on the name of the attribute. None is a special key in this dict, its value will be used for all the attributes not specified explicitly in the dictionary.
	
##16. union(graphs)
Creates the union of two (or more) graphs.

	parameters:
	graphs - the list of graphs to be united with the current one.
	
##17. vcount()
Counts the number of vertices.

	return the number of vertices in the graph.
	
##18. write_edgelist(f)
Writes the edge list of a graph to a file.
Directed edges are written in (from, to) order.

	parameters:
	f - the name of the file to be written or a Python file handle.
	

	
	
		
	
