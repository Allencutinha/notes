# common Path planning Algorithms
+ **A * Algorithm:** As discussed earlier, A* is a popular algorithm for finding the shortest path between two points in a graph. It is often used in combination with other techniques such as occupancy grids, road network maps, and dynamic programming to plan safe and efficient paths for self-driving cars.

+ **Rapidly-Exploring Random Trees (RRT):** RRT is a probabilistic algorithm that generates a tree of randomly sampled points in the search space. It is often used for obstacle avoidance and path planning in complex and dynamic environments.

+ **Hybrid A* Algorithm:** Hybrid A* is a variant of the A* algorithm that takes into account the motion dynamics of the vehicle. It combines the benefits of discrete search algorithms (such as A*) with continuous control algorithms to plan feasible and smooth paths for self-driving cars.

+ **Dynamic Window Approach (DWA):** DWA is a local path planning algorithm that takes into account the current state of the vehicle and its surroundings to generate safe and feasible paths. It uses a dynamic window concept to limit the search space and reduce the computation time.

+ **Model Predictive Control (MPC):** MPC is a control-based path planning algorithm that predicts the future behavior of the vehicle and optimizes the trajectory accordingly. It is often used for high-speed and precision driving applications.

# A* Algorithm

The A* algorithm is a widely used pathfinding algorithm in artificial intelligence and robotics. It is a variant of Dijkstra's algorithm and is used to find the shortest path between two nodes in a graph, taking into account both the cost of reaching the nodes and an estimate of the distance to the destination node.

The A* algorithm uses a heuristic function to estimate the distance from a given node to the destination node. This function is called the "h-value" and it guides the algorithm towards the goal, by prioritizing the nodes that are closer to the goal. The algorithm maintains two lists: the open list, which contains the nodes that are to be evaluated, and the closed list, which contains the nodes that have already been evaluated.

At the beginning, the start node is added to the open list, with a cost of zero and an estimated distance to the goal (h-value). Then, the algorithm evaluates the nodes in the open list, selecting the node with the lowest cost (including the h-value) and moving it to the closed list. For each neighboring node that is not in the closed list, the algorithm computes the cost of reaching that node from the current node and the estimated distance to the goal. If this cost is lower than the current cost of the neighboring node (or the node is not yet in the open list), the neighbor is added to the open list with its new cost and its parent set to the current node. This process continues until the goal node is found or the open list is empty.

The A* algorithm guarantees to find the shortest path if the heuristic function satisfies some conditions, such as being admissible (never overestimating the distance to the goal) and consistent (the estimated distance from any node to the goal is less than or equal to the sum of the estimated distance to its neighbor and the cost of moving to that neighbor). A* is a complete algorithm, meaning it will always find a solution if one exists. However, it may be slow in some cases due to the large number of nodes that may need to be evaluated.


# D* Algorithm

D* (pronounced "D-star") is a real-time incremental search algorithm, used to find the shortest path between two nodes in a graph. It is an improvement over the A* algorithm and is particularly useful in dynamic environments, where the cost of moving from one node to another may change during the search process.

The D* algorithm maintains a map of the graph, along with the current costs of moving from each node to its neighbors. It also maintains two lists of nodes: the "open list," which contains the nodes that still need to be explored, and the "closed list," which contains the nodes that have already been explored.

At the beginning, the start node is added to the open list with a cost of zero. The algorithm then repeatedly selects the node with the lowest cost in the open list and explores its neighboring nodes. If the cost of moving from the current node to a neighboring node has changed since the last time that node was visited, the algorithm updates the cost of that node and adds it back to the open list. If the cost of moving from the current node to a neighboring node has not changed, the algorithm simply skips over that node.

Once the goal node is reached, the algorithm can terminate. If the costs of moving from a node to its neighbors change during the search process, the algorithm can be re-run from the affected nodes to update the path. This makes D* a useful algorithm for dynamic environments, where the cost of moving between nodes may change frequently.

One important feature of D* is that it is a complete algorithm, meaning that it will always find a solution if one exists, and it will find the shortest path under certain conditions. However, the performance of D* can be slower than A* in some cases due to the need to continuously update the costs of nodes as the search progresses.

