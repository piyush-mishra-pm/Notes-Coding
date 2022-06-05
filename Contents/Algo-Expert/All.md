### 1. Two Number Sum:

**Problem**: Given total sum, find a pair of numbers in an array summing to that total sum. </br>
**Example**: For [-4,-1,1,3,5,6,8,11] {10} , ans is [11,-1]. </br>
**Solutions**: </br>

1. Approach 1: Double for loop. T: O(N^2); S O(1).
2. Approach 2: HashSet. T: O(N); S O(N).
3. Approach 3: Sort and Two pointer. T: O(NlogN); S:O(1).
   </br>

---

</br>

### 2. Validate Subsequence:

**Problem**: Check if given subsequence is valid for an array. Subsequence contains array elements in order, but some elements might be skipped.</br>

**Example**: For arr [5,1,22,25,6,-1,8,10] and subseq [1,6,-1,10], ans is true.</br>

**Solutions**:</br>

1. Approach 1: Linear scan of array and check if subseq element is present in order. T: O(N); S:O(1).
   </br>

---

### 3. Sorted Squared Array:

**Problem**: Given sorted a array of int, return its sorted squared int array. Do not modify the input array.</br>
**Example**: For arr [-2,-1,1,2,3,5,6,8,9] ans is [1,1,4,4,9,25,36,64,81]].</br>
**Solutions**:</br>

1. Approach 1: Generate new array with squared values, and then sort that array. T: O(NlogN) ; S: O(N).
2. 2 Pointer, and comparing absolute values. T: O(N) ; S:O(N).
   </br>

---

### 4. Tournament Winner:

**Problem**: Competition and results array given, tell which team is winner. Guaranteed that there is a winner (no tie).</br>
**Example**: For competition Array [[[[ "HTML" ,  "C#"],["C#","python"],["python","HTML"]]]] and results array is [0,0,1]. Answer for winner is "python".</br>
**Solutions**:</br>

1. Approach 1: Hashmap of Team and score. Also keep track of maximum score team on every update of team score. T: O(N) ; S:O(K). (N competitions and K teams).
   </br>

---

### 5. Non-Constructible Change:

**Problem**: Minimum change that cannot be created, considering all the coins available as given in an array. Cannot reuse a coin.</br>
**Example**: For coins array [5,7,1,1,2,3,22], ans is 4.</br>
**Solutions**:</br>

1. Approach 1: Try out in sequence, whether it is possible to construct a sum. Very complicated.
2. Approach 2: Sort the coin array first. If any new coin is greater than C+1 (C is coins cum sum), then we can't create C+1 coin. T: O(NlogN) ; S: O(1).

```java
Arrays.sort(coins);
int currentChangeCreated=0;
for(coin in coins){
	if(coin > currentChangeCreated + 1)
		return currentChangeCreated + 1;
	currentChangeCreater += coin;
}
return currentChangeCreated + 1;
```

</br>

---

### 6. Find Closest Value in BST:

**Problem**: Given a BST, and a target value, find the closest value to target, present in BST. </br>
**Solutions**:</br>

1. Approach 1: Visit all BST nodes and track number with smallest absolute difference. T: O(N) ; S: O(1).
2. Approach 2: If BST node smaller than target, then can eliminate firther search to left of BST node. T: O(N) {for skewed BST, but logN on avg} ; S: (N) {for recursion call stack sweked, but on avg O(logN)}.
3. Approach 3: Iteratively traverse BST. T:O(N); S:O(1).

```java
// Recursive:
private int helper(TreeNode node, int target, int closestNodeVal){
	// Reached end of BST:
	if(node == null) return closestNodeVal;
	// Update the closest value, if current node is appropriate for that.
	if(Math.abs(target - closestNodeVal) > Math.abs(target - node.value)
		closestNodeVal = node.val;
	// if current node too big, then go left:
	if(target < node.value)
		return helper(node.left, target, closestNodeVal);
	// if current node too small, then go right:
	else if(target > node.val)
		return helper(node.right, target, closestNodeVal);
	// current node === target
	else
		return closestNodeVal;
}
// Iterative:
private int helper(TreeNode node, int target){
	closestNodeVal = Integer.MAX_VALUE;
	currentNode = node;
	while(currentNode != null){
		// Update the closest value, if current node is appropriate for that.
		if(Math.abs(target - closestNodeVal) > Math.abs(target - node.value)
			closestNodeVal = currentNode.val;
		// if current node too big, then go left:
		if(target < node.value)
			currentNode = currentNode.left;
		// if current node too small, then go right:
		else if(target > node.val)
			currentNode = currentNode.right;
		// current node === target
		else
			break;
	}
	return closestNodeVal;
}
```

</br>

---

### 7. Branch Sums of Tree:

**Problem**: Given a Tree, return the sum of all branches (from root to leaf) as a list. </br>
**Solutions**: </br>

1. Approach 1: Traverse all nodes of tree in inorder traversal, and keep trac of running sum. On reaching the leaf node, append branch sum to list of branch sums. T: O(N) ; S: O((N + Num\_ of_Leaf nodes) <= 2N => so, N) (skewed tree). </br>
   </br>

---

### 8. Node Depths:

**Problem**: Given a Binary Tree, return the sum of node depths of all nodes of the tree. Here, node depth of tree is the distance between root and node of that tree.</br>
**Solutions**:</br>

1. Approach 1: Recursion. T: O(N) ; S: O(h).
2. Approach 2: Iteration, using a Stack. T:O(N) ; S:O(h).

```java
private int nodeDepth(TreeNode node, int depth=0){
	if(root == null) return 0;
	return depth + nodeDepth(node.left,depth+1) + nodeDepth(node.right,depth+1) ;
}
```

</br>

---

### 9. Depth first search on n-ary Tree:

**Problem**: Given a n-ary Tree, return an array containing DFS traversal. </br>
**Solutions** : </br>

1. Approach 1: Recursion with inorder traversal. T: O(N) ; S: O(h). </br>

```java
private ArrayList<Integer> list = new ArrayList<>();

private void dfs(TreeNode node){
	if(node == null) return;

	list.append(node.val);

	for(TreeNode child : node.children){
		dfs(child);
	}
}
```

</br>

---
