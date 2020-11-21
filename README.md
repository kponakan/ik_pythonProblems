# Complete the minNumberOfRolls function below.
from collections import deque
def minNumberOfRolls(n, moves):
    #BFS problem, 
    visited = [-1] *n
    
    if n == 1:
        return 0
        
    que = deque()
    que.append([0,0])
    visited[0] = 1
    
    while que:
        currnode, result = que.popleft()
        if currnode == n-1:
            return result
        
        for neighbor in range(currnode+1,min(currnode+7,n)):
            if visited[neighbor] == -1:
                visited[neighbor] = 1
                if moves[neighbor] == -1:
                    que.append([neighbor,result+1])
                else:
                    que.append([moves[neighbor],result+1])
    
    return -1                
    
    
