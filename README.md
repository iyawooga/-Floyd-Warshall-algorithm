Floyd-Warshall algorithm for a 4x4 distance matrix (this #includes the route matrices for each iteration) :
#input 0 when row and column index are the same
#input inf when there are no direct path between nodes
def tables():
  global distance_matrix
  global route_matrix_1
  node_paths=[['A','A','A','A'],['B','B','B','B'],['C','C','C','C'],['D','D','D','D']]
  route_matrix_1=[['A','B','C','D'],['A','B','C','D'],['A','B','C','D'],['A','B','C','D']]
  distance_matrix=[[],[],[],[]]
  for rows in range(4):
    for columns in range(4):
      num=float(input(f"distance {node_paths[rows][columns]}{node_paths[columns][rows]}: "))
      distance_matrix[rows].append(num)
tables()
for z in range(4):
  print(distance_matrix[z])


completed=[[],[],[],[]]

def first_iteration():
  global completed
  for i in range(4):
    for j in range(4):
      sum=distance_matrix[i][0]+distance_matrix[0][j]
      if sum<distance_matrix[i][j]:
        completed[i].append(sum)
        route_matrix_1[i][j]=route_matrix_1[i][0]
      else:
        completed[i].append(distance_matrix[i][j])

  print("iteration 1: ")
  for x in range(4):
    print(completed[x])
  print("route matrix 1: ")
  for y in range(4):
      print(route_matrix_1[y])

first_iteration()

def second_iteration():
  for i in range(4):
    for j in range(4):
      sum=completed[i][1]+completed[1][j]
      if sum<completed[i][j]:
        completed[i][j]=sum
        route_matrix_1[i][j]=route_matrix_1[i][1]
  print("iteration 2: ")
  for x in range(4):
    print(completed[x])
  print("route matrix 2: ")  
  for y in range(4):
      print(route_matrix_1[y])

second_iteration()

def third_iteration():
  for i in range(4):
    for j in range(4):
      sum=completed[i][2]+completed[2][j]
      if sum<completed[i][j]:
        completed[i][j]=sum
        route_matrix_1[i][j]=route_matrix_1[i][2]
  print("third iteration: ")
  for x in range(4):
    print(completed[x])
  print("route matrix 3: ")
  for y in range(4):
      print(route_matrix_1[y])

third_iteration()

def fourth_iteration():
  for i in range(4):
    for j in range(4):
      sum=completed[i][3]+completed[3][j]
      if sum<completed[i][j]:
        completed[i][j]=sum
        route_matrix_1[i][j]=route_matrix_1[i][3]
  print("final iteration: ")
  for x in range(4):
    print(completed[x])
  print("route matrix 4: ")
  for y in range(4):
      print(route_matrix_1[y])

fourth_iteration()
