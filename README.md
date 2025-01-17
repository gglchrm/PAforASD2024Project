# PAforASD2024Project
## 1. Algorithm, parallelization method
DAG Topological Sort, also known as topological ordering, is an algorithm that arranges the vertices (nodes) of a Directed Acyclic Graph (DAG) in a linear order such that for every directed edge in the graph.

The basic idea behind topological sorting is to identify the nodes with no incoming edges (i.e., nodes with zero indegree), process those nodes, then remove their outgoing edges and repeat until all nodes are processed.

Here’s a step-by-step explanation of how topological sorting works:

1. Identify Nodes with Zero Indegree: Start by finding all nodes that have no incoming edges. These nodes can be processed immediately since they don’t depend on any other nodes.
   
2. Process and Remove: Process these nodes and add them to the sorted list. Then, remove all outgoing edges from these nodes.

3. Update Indegrees: Update the indegree count of all nodes whose incoming edges were removed. If any node now has zero indegree, move to step 1.

4. Repeat Until All Nodes Are Processed: Continue this process until all nodes have been added to the sorted list.

 Kahn’s Algorithm (BFS-based):
   - Maintain a queue of nodes with zero indegree.
   - Process nodes from the queue, removing their outgoing edges and updating the indegrees of their neighbors.
   - Add new nodes with zero indegree to the queue.


## 2. How to reproduce results and start an algorithm. Where and in which format data should be placed.
To reproduce result you need to launch DAG_topological_sort.ipynb. In this file first cells is DAG-generator from https://github.com/Livioni/DAG_Generator, you can generate dataset by youself. 
There is DAG_dataset_100k.txt in this repo.

## 3. What part of the alg parallel
Khan's method by itself is poorly suited for parallelization because it assumes sequential vertex processing. We use the multiprocessing module to create a pool of workflows. Each process gets its own copy of the queue and result list through Manager.

## 4. Speedup calculation -- dependency between number of threads/processes/workers and speedup (linear version time / parallel version time)
Regular algo  --       0.612140 sec

Parallel allgo time -- 0.525991 sec
