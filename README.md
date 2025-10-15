
def f(x):
    return -(x - 3)**2 + 10

def get_neighbors(x):
    return [x - 1, x + 1]

def hill_climb_dfs(current, visited=None):
    if visited is None:
        visited = set()
    visited.add(current)
    current_val = f(current)
    neighbors = sorted(get_neighbors(current), key=lambda n: f(n), reverse=True)
    for neighbor in neighbors:
        if neighbor not in visited and f(neighbor) > current_val:
            return hill_climb_dfs(neighbor, visited)
    return current, current_val

start = 0
best_x, best_val = hill_climb_dfs(start)
print(best_x, best_val)
