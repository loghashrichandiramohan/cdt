class BlocksWorld: 
 def __init__(self, initial_state): 
 self.state = initial_state 
 def display_state(self): 
 for row in self.state: 
 print(" ".join(row)) 
 print() 
 def is_goal_state(self, goal_state): 
 return self.state == goal_state 
 def generate_successors(self): 
 successors = [] 
 for i in range(len(self.state)): 
 for j in range(len(self.state[i])): 
 if self.state[i][j] != " ": 
 # Try moving the block up 
 if i > 0 and self.state[i - 1][j] == " ": 
 new_state = [row.copy() for row in self.state] 
 new_state[i][j], new_state[i - 1][j] = new_state[i - 1][j], new_state[i][j] 
 successors.append(BlocksWorld(new_state)) 
 # Try moving the block down 
 if i < len(self.state) - 1 and self.state[i + 1][j] == " ": 
 new_state = [row.copy() for row in self.state] 
 new_state[i][j], new_state[i + 1][j] = new_state[i + 1][j], new_state[i][j] 
 successors.append(BlocksWorld(new_state)) 
 # Try moving the block left 
 if j > 0 and self.state[i][j - 1] == " ": 
 new_state = [row.copy() for row in self.state] 
 new_state[i][j], new_state[i][j - 1] = new_state[i][j - 1], new_state[i][j] 
 successors.append(BlocksWorld(new_state)) 
 # Try moving the block right 
 if j < len(self.state[i]) - 1 and self.state[i][j + 1] == " ": 
 new_state = [row.copy() for row in self.state] 
 new_state[i][j], new_state[i][j + 1] = new_state[i][j + 1], new_state[i][j] 
 successors.append(BlocksWorld(new_state)) 
 return successors 
def depth_first_search(initial_state, goal_state): 
 stack = [BlocksWorld(initial_state)] 
 visited = set() 
 while stack: 
 current_state = stack.pop() 
 if current_state.is_goal_state(goal_state): 
 print("Goal state reached:") 
 current_state.display_state() 
 return True 
 visited.add(tuple(map(tuple, current_state.state))) 
 successors = current_state.generate_successors() 
 for successor in successors: 
 if tuple(map(tuple, successor.state)) not in visited: 
 stack.append(successor) 
 print("Goal state not reachable.") 
 return False 
# Example usage: 
initial_state = [ 
 ["A", "B", " "], 
 ["C", " ", "D"], 
] 
goal_state = [ 
 [" ", "B", "A"], 
 ["C", "D", " "], 
] 
depth_first_search(initial_state, goal_state) 
