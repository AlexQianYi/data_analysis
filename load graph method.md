##Load graph efficiently

#step 1
get the nodeID of every file.
delete prefix and suffix of file path.
	
	nodeID = gsub("Edges/", "", file)
	nodeID = as.numeric(gsub(".edges", "", nodeID))
	IDlist = c(IDlist, nodeID)
		
#step 2
visit every file and save node and edge in two structure. 
save every node in *IDlist* and save every path in *relations*

	 tempEdge = data.frame(from=nodeID, to=temp)
	 IDlist = c(IDlist, temp)
	 relations = rbind(relations, tempEdge)
   
#step 3
simlify graph, remove double edges in graph.

	g = simplify(g)