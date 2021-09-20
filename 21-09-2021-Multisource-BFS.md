# Multisource BFS

Learned about this new algorithm today. Pretty similar to standard breadth first search, with only difference that we have multiple start points. 
Something like when you want to do BFS from multiple nodes in one pass only. 

This whole algorithm can be replaced by a for loop over the nodes acting as source, and in each iteration we do bfs on the node. The time complexity will be same, though the space complexity can vary. Sometimes its prefereble to go the multisource way.

As far as implementation is concerned, whole algorithm is same, except that now we have all the source nodes in the queue intially.

One more nice approach I read in a codeforces discuss is using a fake source and connecting all the sources to that node. Now proceed same as standard BFS but from the fake source
Only thing to take care of is to subtract that extra 1 added because of the fake source.

![img](https://codeforces.com/predownloaded/a5/e9/a5e9c9467ef6b37f122f8b6da0621b54775dc608.png)

A nice problem for this case is -
[As far from land as possible](https://leetcode.com/problems/as-far-from-land-as-possible)
My solution for this (faster than 73% at best)


      class Solution {
      public:
      int maxDistance(vector<vector<int>>& grid) {
      	queue<pair<int32_t, int32_t>> cache;
      	bool hasWater = 0;
      	for (size_t i = 0; i < grid.size(); i++)
      	{
      		for (size_t j= 0; j < grid[i].size(); j++)
      		{
      			if(grid[i][j] == 1) 
      			{
      				cache.push(make_pair(i, j));
      				grid[i][j] = -1;
      			}
      			else 
      			{
      				hasWater = 1;
      			}
      		}
      	}
      
      	if (!hasWater || cache.empty()) { return -1; }
      
      	vector<pair<int32_t, int32_t>> dir = { {-1,0},{0,1},{1,0},{0,-1} };
      	
      	int32_t distance = 0;
      	
      	while(!cache.empty()) 
      	{
      		pair<int32_t, int32_t> index = cache.front();
      		cache.pop();
      		for (size_t i = 0; i < dir.size(); i++)
      		{
      			pair<int32_t, int32_t> node = make_pair(index.first + dir[i].first, index.second + dir[i].second);
      			if((node.first >= 0 && node.first < grid.size()) && (node.second >= 0 && node.second < grid[0].size()))
      			{
      				if(grid[node.first][node.second] == 0) 
      				{
      					if(grid[index.first][index.second] == -1) 
      					{
      						grid[node.first][node.second]++;
      						if (grid[node.first][node.second] > distance) { distance = grid[node.first][node.second]; }
      					}
      					else 
      					{
      						grid[node.first][node.second] = grid[index.first][index.second] + 1;
      						if (grid[node.first][node.second] > distance) { distance = grid[node.first][node.second]; }
      					}
      					cache.push(node);
      				}
      			}
      		}
      	}
      
      	return distance;
      }
      };
      
