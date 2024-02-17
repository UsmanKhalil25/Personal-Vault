#### Important terminologies
**agent**
- agent is an entity that perceives its environment and acts upon that environment
- for example in puzzle that requires some tiles to be moved the agent is the human or AI solving the puzzle 
**state**
- any configuration of the problem that is being solved
**initial state**
- the state from where the agent starts solving the problem
**actions**
- choice that can be made at each state
**actions(s)**
- actions(s) returns the set of all the actions that can be taken at state s

``Note that we need some encoding of how the state and actions are relating from one another

**transition model**
- what state we get after we perform some action in a given state(current state)
- a description of what state results from performing any applicable action in any state
**result(s,a)**
- return the state resulting from the action a in state s
**state space**
- the set of all states reachable from the initial state by any sequence of actions
**goal test**
- we need some way to determine that our AI has reached the solved state or goal state
- so a goal test way to determine whether a given state is a goal state
**path cost**
- when solving a search problem we need our AI to give the most low path cost solution
- numerical cost associated with a given path
#### use of graphs
- we can use graphs to solve the problem
- each node (vertex) represents each state and each edge from a node to b node shows that state b is reachable from a state
- the weight on each edge is the cost that adds to the path
**optimal solution**
- the solution with lowest path cost
#### Search Problems
- initial state
	- the state where we start
- actions
	- the action or set or actions that can be taken at some state 
- transition model
	- way of defining what state to we end up on when we perform actions on a present state
- goal test
	- to know whether or not we have reached our goal or not
- path cost function
	- a function that helps use to now the cost of solution

#### node
- a data structure that keeps track of 
	- a state
	- a parent (node that generated this node)
	- an action(action applied to parent to get node)
	- a path cost (from initial state to node)

#### frontier
- nodes can only contain information
- we need the **frontier**, the mechanism that “manages” the _nodes_. 
- in bfs we have used queue as frontier in c++  
#### Approach
- start with a frontier that contain the initial state
- Repeat:
	- if the frontier is empty then no solution
		- if empty then no solution
	- remove a node from the frontier
	- if node contains goal state, return the solution
	- expand node, add resulting nodes to the frontier
		- adding the adjacent nodes to the frontier

`Note: we also need to keep track of the nodes we have already visited this will prevent going back and forth if there happens to be two edges between two nodes say a and b`
#### Revised approach
- start with a frontier that contain the initial state
- start with an empty explored set
- Repeat:
	- if the frontier is empty then no solution
		- if empty then no solution
	- remove a node from the frontier
	- if node contains goal state, return the solution
	- add the node to the explored set
	- expand node, add resulting nodes to the frontier if they are not already in the frontier or explored set
		- adding the adjacent nodes to the frontier

#### Depth first search
- search algorithm that always expands the deepest node in the frontier
#### Breath first search
- search algorithm that always expand the shallowest node in the frontier

#### Uninformed Search
- search strategy that uses no problem specific knowledge
- BFS and DFS are uninformed search

#### Informed Search
- search strategy that uses problem specific knowledge to find the solution

#### Greedy best-first search
- search algorithm that expands the node that is closest to the goal, as estimated by a heuristic function h(n)
- the heuristic functions makes decision based on the distance of a specific block from the goal (if we have a grid suppose then the x,y co-ordinates help) also know as manhattam distance

#### A* search
- search algorithm that expands node with lowest value of g(n) + h(n)
	- g(n) = cost to reach node(number of steps to reach that node)
	- h(n) = estimated cost to goal(Manhattan distance)
- optimal if:
	- h(n) is admissible (never overestimate the true cost)
	- h(n) is consistent (for every node n and successor n' with step cost c , h(n)<=h(n') + c)

#### Adversarial Search
- where we have two agents
- the two agents are mostly acting opposite to each other

#### Mini-max 
- Max(X) aims to maximize score
- Min(O) aims to minimize the score
- ###### Tick- Tac - Toe
	- So: initial state
	- Player(s): return which player to move in state s
		- tells us which players turn it is using s
	- actions(s): returns legal moves in state s
	- result(s,a): returns state after action a is taken in state s
	- terminal(s): checks if state s is a terminal state
	- utility(s): final numerical value for terminal state s
- ###### Algorithm
	- Given a state s:
		- **Max** picks action **a** in **actions(s)** that produces highest value of **min-value(result(s, a))**
		- **Min** picks action **a** in **actions(s)** that produces smallest value of **max-value(result(s, a))**
	- function max_value(state):
		- if terminal(state):
			- return utility(state)
		- v = INT_MIN(minimum) or negative infinity
		- for action in **actions(state)**:
			- v = max(v, min_value(result(state, action)))
			return v
	- function min_value(state):
		- if terminal(state):
			- return utility(state)
		- v = INT_MAX(maximum) or positive infinity
		- for action in **actions(state)**:
			- v = min(v, max_value(result(state, action)))
			return v

`Look up for aplha-beta pruning and depth-limited minimax in harvard note 0`