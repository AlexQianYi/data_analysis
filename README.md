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
	
##6. alpha_centrality(graph, nodes=V(graph), alpha=1, loops=FALSE, exo=1, weights=NULL, tol=1e-07, sparse=TRUE)
alpha_centrality calculates the alpha centrality of some (or all) vertices in a graph.

	parameter
	graph - The input graph, can be directed or undirected.
	node - Vertex sequence, the vertices for which the alpha centrality values are returned. (For technical reasons they will be calculated for all vertices, anyway.)
	alpha - Parameter specifying the relative importance of endogenous versus exogenous factors in the determination of centrality. See details below.
	loops - Whether to eliminate loop edges from the graph before the calculation.
	exo - The exogenous factors, in most cases this is either a constant – the same factor for every node, or a vector giving the factor for every vertex. Note that too long vectors will be truncated and too short vectors will be replicated to match the number of vertices.
	weights - A character scalar that gives the name of the edge attribute to use in the adjacency matrix. If it is NULL, then the ‘weight’ edge attribute of the graph is used, if there is one. Otherwise, or if it is NA, then the calculation uses the standard adjacency matrix.
	tol - Tolerance for near-singularities during matrix inversion, see solve.
	sparse - Logical scalar, whether to use sparse matrices for the calculation. The ‘Matrix’ package is required for sparse matrix support.
	
##7. dfs(graph, root, neimode=c('out', "in", 'all', 'total'), unreachable=TRUE, order=TRUE, order.out=FALSE, father=FALSE, dist=FALSE, in.callback=NULL, out.callback=NULL, extra=NULL, rho=parent.frame())
Depth-first search is an algorithm to traverse a graph. It starts from a root vertex and tries to go quickly as far from as possible.

	parameter
	graph - The input graph.
	root - The single root vertex to start the search from.
	neimode - For directed graphs specifies the type of edges to follow. ‘out’ follows outgoing, ‘in’ incoming edges. ‘all’ ignores edge directions completely. ‘total’ is a synonym for ‘all’. This argument is ignored for undirected graphs.
	unreachable - Logical scalar, whether the search should visit the vertices that are unreachable from the given root vertex (or vertices). If TRUE, then additional searches are performed until all vertices are visited.
	order - Logical scalar, whether to return the DFS ordering of the vertices.
	order.out - Logical scalar, whether to return the ordering based on leaving the subtree of the vertex.
	father - Logical scalar, whether to return the father of the vertices.
	dist - Logical scalar, whether to return the distance from the root of the search tree.
	in.callback - If not NULL, then it must be callback function. This is called whenever a vertex is visited. See details below.
	out.callback - If not NULL, then it must be callback function. This is called whenever the subtree of a vertex is completed by the algorithm. See details below.
	extra - Additional argument to supply to the callback function.
	rho - The environment in which the callback function is evaluated.
	
##8. bfs(graph, root, neimode=c('out', 'in', 'all', 'total'), unreachable=TRUE, restricted=NULL, order=TRUE, rank=FALSE, father=FALSE, pred=FALSE, succ=FALSE, dist=FALSE, callback=NULL, extra=NULL, rho=parent.frame())
Breadth-first search is an algorithm to traverse a graph. We start from a root vertex and spread along every edge “simultaneously”.

	parameter
	graph - The input graph.
	root - Numeric vector, usually of length one. The root vertex, or root vertices to start the search from.
	neimode - For directed graphs specifies the type of edges to follow. ‘out’ follows outgoing, ‘in’ incoming edges. ‘all’ ignores edge directions completely. ‘total’ is a synonym for ‘all’. This argument is ignored for undirected graphs.
	unreachable - Logical scalar, whether the search should visit the vertices that are unreachable from the given root vertex (or vertices). If TRUE, then additional searches are performed until all vertices are visited.
	restricted - NULL (=no restriction), or a vector of vertices (ids or symbolic names). In the latter case, the search is restricted to the given vertices.
	order - Logical scalar, whether to return the ordering of the vertices.
	rank - Logical scalar, whether to return the rank of the vertices.
	father - Logical scalar, whether to return the father of the vertices.
	pred - ogical scalar, whether to return the predecessors of the vertices.
	succ - Logical scalar, whether to return the successors of the vertices.
	dist - Logical scalar, whether to return the distance from the root of the search tree.
	callback - If not NULL, then it must be callback function. This is called whenever a vertex is visited. See details below.
	extra - Additional argument to supply to the callback function.
	rho - The environment in which the callback function is evaluated.
	

##9. is.directed(graph)
determine whether a graph is directed

##10. is.weighted(graph)
determine whether a graph is weighted

##11. is.simple(graph)
Simple graphs are graphs which do not contain loop and multiple edges.

##12. closeness(graph, vids=V(graph), mode=c('out', 'in', 'all', 'total'), weights=NULL, normalized=FALSE)
Cloness centrality measures how many steps is required to access every other vertex from a given vertex.

	parameter
	graph - The graph to analyze.
	vids - The vertices for which closeness will be calculated.
	mode - Character string, defined the types of the paths used for measuring the distance in directed graphs. “in” measures the paths to a vertex, “out” measures paths from a vertex, all uses undirected paths. This argument is ignored for undirected graphs.
	weights - Optional positive weight vector for calculating weighted closeness. If the graph has a weight edge attribute, then this is used by default.
	normalized - Logical scalar, whether to calculate the normalized closeness. Normalization is performed by multiplying the raw closeness by n-1, where n is the number of vertices in the graph.
	cutoff - The maximum path length to consider when calculating the betweenness. If zero or negative then there is no such limit.
	
##13. is.connected(graph)
determine whether a graph is connected

##14. ego(graph, order, nodes=V(graph), mode=c('all', 'out'. 'in'), mindist=0)
These functions find the vertices not farther than a given limit from another fixed vertex, these are called the neighborhood of the vertex.

	parameter
	graph - The input graph.
	order - Integer giving the order of the neighborhood.
	nodes - The vertices for which the calculation is performed.
	mode - Character constatnt, it specifies how to use the direction of the edges if a directed graph is analyzed. For ‘out’ only the outgoing edges are followed, so all vertices reachable from the source vertex in at most order steps are counted. For ‘"in"’ all vertices from which the source vertex is reachable in at most order steps are counted. ‘"all"’ ignores the direction of the edges. This argument is ignored for undirected graphs.
	mindist - The minimum distance to include the vertex in the result.
	
##15. power_centrality(graph, nodes=V(graph), loops=FALSE, exponent=1, rescale=FALSE, tol=1e-07, sparse=TRUE)
power_centrality takes a graph (dat) and returns the Boncich power centralities of positions (selected by nodes). The decay rate for power contributions is specified by exponent (1 by default).

	parameter
	graph - the input graph.
	nodes - vertex sequence indicating which vertices are to be included in the calculation. By default, all vertices are included.
	loops - boolean indicating whether or not the diagonal should be treated as valid data. Set this true if and only if the data can contain loops. loops is FALSE by default.
	exponent - exponent (decay rate) for the Bonacich power centrality score; can be negative
	rescale - if true, centrality scores are rescaled such that they sum to 1.
	tol - tolerance for near-singularities during matrix inversion (see solve)
	sparse - Logical scalar, whether to use sparse matrices for the calculation. The ‘Matrix’ package is required for sparse matrix support