# Ex.No: 4 Implementation of Alpha Beta Pruning

REGISTER NUMBER : 212222040046

# AIM:
Write a Alpha beta pruning algorithm to find the optimal value of MAX Player from the given graph.

# ALGORITHM:

    Start the program
    Initially assign MAX and MIN value as 1000 and -1000.
    Define the minimax function using alpha beta pruning
    If maximum depth is reached then return the score value of leaf node. [depth taken as 3]
    In Max player turn, assign the alpha value by finding the maximum value by calling the minmax function recursively.
    In Min player turn, assign beta value by finding the minimum value by calling the minmax function recursively.
    Specify the score value of leaf nodes and Call the minimax function.
    Print the best value of Max player.
    Stop the program.

# Program:
```
class GraphNode:
    def __init__(self, value, children=[]):
        self.value = value
        self.children = children

def alpha_beta(node, alpha, beta, maximizing_player):
    if node is None:
        return None
    
    if len(node.children) == 0:
        return node.value
    
    if maximizing_player:
        value = float('-inf')
        for child in node.children:
            value = max(value, alpha_beta(child, alpha, beta, False))
            alpha = max(alpha, value)
            if alpha >= beta:
                break
        return value
    else:
        value = float('inf')
        for child in node.children:
            value = min(value, alpha_beta(child, alpha, beta, True))
            beta = min(beta, value)
            if alpha >= beta:
                break
        return value


node1 = GraphNode(3)
node2 = GraphNode(6)
node3 = GraphNode(2)
node4 = GraphNode(8)
node5 = GraphNode(2)
node6 = GraphNode(3)
node7 = GraphNode(5)
node8 = GraphNode(9)

node1.children = [node2, node3]
node2.children = [node4, node5]
node3.children = [node6, node7]
node4.children = [node8]
```
# Start alpha-beta pruning
```
optimal_value = alpha_beta(node1, float('-inf'), float('inf'), True)
print("Optimal value for MAX player:", optimal_value)
```
# Output:
![318407976-87803fe9-6e83-4deb-a392-eb5aebc24965](https://github.com/user-attachments/assets/f8e8d706-2735-4978-8611-1583fb6e4ac3)


# Result:
Thus the best score of max player was found using Alpha Beta Pruning.
