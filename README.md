# data_analysis

# igraph method in R
##1. betweenness(graph, v=V(graph), directed=True, weights=NULL, nobigint=TRUE, normalized=FALSE)
The vertex and edge betweenness are (roughly) defind by the number of geodesices (shortest paths) going though a vetex or an edge.

	parameter
	graph - The graph to analyze
	v - the vertices for which the vertex betweenness will be calculated.
	directed - logical, wheter directed paths should be considered while dertermining the shortest paths.
	weights - Optional positive weight vector for calculating weighted betweenness. If the graph has a weight edge attribute , then this is used be default.
	nobigint - Logical scalar, whether to use big integers during the calculation. This is only required for lattice-like graphs that have very many shortest paths between a pair of vertices. If TRUE (the default), then big integers are not used.
	normalized - Logical scalar, whether to normalize the betweenness scores. If TRUE, then the results are normalized according to Bnorm=2*B/(n*n-3*n+2) , where Bnorm is the normalized, B the raw betweenness, and n is the number of vertices in the graph.
	
##2. ecount(graph)
count the edge of graph

##3. get_diameter(graph, directed=TRUE, unconnected=TRUE, weights=NULL)
get the path of diameter of graph

	parameter
	graph - The graph to analyze.
	directed - Logical, whether directed or undirected paths are to be considered. This is ignored for undirected graphs.
	unconnected - Logical, what to do if the graph is unconnected. If FALSE, the function will return a number that is one larger the largest possible diameter, which is always the number of vertices. If TRUE, the diameters of the connected components will be calculated and the largest one will be returned.
	weights - Optional positive weight vector for calculating weighted distances. If the graph has a weight edge attribute, then this is used by default.
	
##4. max_cliques(graph, min=NULL, max=NULL, subset=NULL, file=NULL)
These functions find all, the largest or all the maximal cliques in an undirected graph. The size of the largest clique can also be calculated.

	parameter
	graph - The input graph, directed graphs will be considered as undirected ones, multiple edges and loops are ignored.
	min - Numeric constant, lower limit on the size of the cliques to find. NULL means no limit, ie. it is the same as 0.
	max - Numeric constant, upper limit on the size of the cliques to find. NULL means no limit.
	subset - If not NULL, then it must be a vector of vertex ids, numeric or symbolic if the graph is named. The algorithm is run from these vertices only, so only a subset of all maximal cliques is returned. See the Eppstein paper for details. This argument makes it possible to easily parallelize the finding of maximal cliques.
	file - If not NULL, then it must be a file name, i.e. a character scalar. The output of the algorithm is written to this file. (If it exists, then it will be overwritten.) Each clique will be a separate line in the file, given with the numeric ids of its vertices, separated by whitespace.
	
##5. simplify(graph, remove.multiple=TRUE, remove.loos=TRUE, edge.attr.comb=igraph_opt("edge.attr.comb"))
Simple graphs are graphs which do not contain loop and multiple edges.

	parameter
	graph - The graph to work on.
	remove.multiple - Logical, whether the multiple edges are to be removed.
	remove.loops - Logical, whether the loop edges are to be removed.
	edge.attr.comb - Specifies what to do with edge attributes, if remove.multiple=TRUE. In this case many edges might be mapped to a single one in the new graph, and their attributes are combined. Please see attribute.combination for details on this.
	