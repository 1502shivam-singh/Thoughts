# Multisource BFS

Learned about this new algorithm today. Pretty similar to standard breadth first search, with only difference that we have multiple start points. 
Something like when you want to do BFS from multiple nodes in one pass only. 

This whole algorithm can be replaced by a for loop over the nodes acting as source, and in each iteration we do bfs on the node. The time complexity will be same, though the space complexity can vary. Sometimes its prefereble to go the multisource way.

As far as implementation is concerned, whole algorithm is same, except that now we have all the source nodes in the queue intially.

One more nice approach I read in a codeforces discuss is using a fake source and connecting all the sources to that node. Now proceed same as standard BFS but from the fake source
Only thing to take care of is to subtract that extra 1 added because of the fake source.

Code coming up in few minutes ....
