# Leetcode
This is a notebook for leetcode learning. :smiley:
## Chapters
### Array
- Binary Search

| Problems | Summary | Times | Others |
| -------- | ------- | ----- | ------ |
| [704. Binary Search](https://leetcode.com/problems/binary-search/) | 基本操作:边界&循环条件；```mid=left+(right-left)/2;(防止溢出) ```| 1 | |
| [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/) | ```insert position(when left==right): left/right+1```| 1 | |
| [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)| | | ⭐ |
|[69. Sqrt(x)](https://leetcode.cn/problems/sqrtx/)|
|[367. Valid Perfect Square](https://leetcode.cn/problems/valid-perfect-square/)|

- Remove Element
双指针法（快慢指针法）
时间复杂度O(n) 空间复杂度O(1)

| Problems | Summary | Times | Others |
| ---| --- | --- | --- |
|[27. Remove Element](https://leetcode.com/problems/remove-element/)| ```if(val!=nums[fastIndex]) nums[slowIndex++]=nums[fastIndex]``` |
|[26. Remove Duplicates from Sorted Array](https://leetcode.cn/problems/remove-duplicates-from-sorted-array/)|
|[283. Move Zeroes](https://leetcode.cn/problems/move-zeroes/)|
|[844. Backspace String Compare](https://leetcode.cn/problems/backspace-string-compare/) | | | ⭐ |
|[977. Squares of a Sorted Array](https://leetcode.cn/problems/squares-of-a-sorted-array/)|

- :o:**Silding Window**
(two pointers)

O(n) 


| Problems | Summary | Times | Others |
| ---| --- | --- | --- |
|[209. Minimum Size Subarray Sum](https://leetcode.cn/problems/minimum-size-subarray-sum/)|一个for循环，窗口起始位置移动规则```while(sum>=target){sum-=nums[i++];}```|| :star: |
|[904. Fruit Into Baskets](https://leetcode.cn/problems/fruit-into-baskets/)|求最大，移动条件：type>2（不满足条件的时候）|| ⭐|
|[76. Minimum Window Substring](https://leetcode.cn/problems/minimum-window-substring/)|```for(const auto &p:mpt)``` 记录start|

### Binary Tree
- Definition:

1. 满二叉树：如果一棵二叉树只有度为0的结点和度为2的结点，并且度为0的结点在同一层上，则这棵二叉树为满二叉树。深度为k，有2^k-1个节点。
2. 在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为第 h 层，则该层包含 1~ 2^(h-1)  个节点。
3. 优先级队列其实是一个堆，堆就是一棵完全二叉树
4. 平衡二叉搜索树：又被称为AVL（Adelson-Velsky and Landis）树，且具有以下性质：它是一棵空树或它的左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。
5. C++中map、set、multimap，multiset的底层实现都是平衡二叉搜索树，所以map、set的增删操作时间时间复杂度是logn;unordered_map底层实现是哈希表。
- How to store a binary tree
可以链式存储，也可以顺序存储
- How to traverse a binary tree

1. 深度优先遍历：前中后序  栈
```
//递归 前序
void traversal(TreeNode* root,vector<int> &v){
      if(root) return;
      v.push_back(root->val);
      traversal(root->left,v);
      traversal(root->right,v);
}
//非递归
//前序:第一次遍历到节点就处理
vector<int> preorderTraversal(TreeNode* root){
       stack<TreeNode*> st;
       if(root) st.push(root);
       vector<int> ans;
       while(!st.empty()){
            TreeNode* node=st.top();
            ans.push_back(node->val);
            st.pop();
            if(node->right) st.push(node->right);
            if(node->left) st.push(node->left);
       }
       return ans;
}
//中序:第二次遍历到(回溯)的时候处理
vector<int> inorderTraversal(TreeNode* root){
        stack<TreeNode*> st;
        TreeNode* cur=root;
        vector<int> ans;
        while(cur||!st.empty()){
             //一直向左遍历
             if(cur){
                st.push(cur);
                cur=cur->left;
             }
             //回溯
             else{
                cur=st.top();
                st.pop();
                ans.push_back(cur->val);
                cur=cur->right;
             }
        }
        return ans;
}
//后序：调整先序左右顺序，逆向输出
vector<int> postorderTraversal(TreeNode* root){
      stack<TreeNode*> st;
      vector<int> ans;
      if(root) st.push(root);
      while(!st.empty()){
            TreeNode* node=st.top();
            st.pop();
            ans.push_back(node->val);
            if(node->left) st.push(node->left);
            if(node->right) st.push(node->right);
      }
      reverse(ans.begin(),ans.end());
      return ans;
}
```
2. 广度优先遍历：层序   队列
```
vector<vector<int>> levelOrderTraversal(TreeNode* root){
      vector<vector<int>> result;
      queue<TreeNode*> que;
      if(root) que.push(root);
      while(!que.empty()){
            vector<int> v;
            int size=que.size();//注意要记录size，因为que.size()在下面for循环过程中可变
            for(int i=0;i<size;i++){
                  TreeNode* node=que.front();
                  que.pop();
                  v.push_back(node->val);
                  if(node->left) que.push(node->left);
                  if(node->right) que.push(node->right);
            }
            result.push_back(v);
      }
      return result;
}
//递归法（深度优先搜索）
void levelOrder(TreeNode* root,vector<vector<int>> &result, int depth){
      if(!root) return;
      if(result.size()==depth) result.push_back(vector<int>());
      result[depth].push_back(root->val);
      levelOrder(root->left,result,depth+1);
      levelOrder(root->right,result,depth+1);
 }
vector<vector<int>> levelOrderTraversal(TreeNode* root){
      vector<vector<int>> result;
      int depth=0;
      levelOrder(root,result,depth);
      return result;
}
```
- Create a Binary Tree
```
struct TreeNode{
    int val;
    TreeNode* Left;
    TreeNode* Right;
    TreeNode(int x): val(x), Left(NULL), Right(NULL) {}
    };
//类    
class Node {
public:
    int val;
    Node* left;
    Node* right;
    Node* next;

    Node() : val(0), left(NULL), right(NULL), next(NULL) {}

    Node(int _val) : val(_val), left(NULL), right(NULL), next(NULL) {}

    Node(int _val, Node* _left, Node* _right, Node* _next)
        : val(_val), left(_left), right(_right), next(_next) {}
};    
    

```
| Problems | Summary | Times | Others |
| ---| --- | --- | --- |
|[515. Find Largest Value in Each Tree Row](https://leetcode.cn/problems/find-largest-value-in-each-tree-row/)|
|[116. Populating Next Right Pointers in Each Node](https://leetcode.cn/problems/populating-next-right-pointers-in-each-node/)|
|[111. Minimum Depth of Binary Tree](https://leetcode.cn/problems/minimum-depth-of-binary-tree/)|dfs/bfs,典型递归||⭐|

```
//111. Minimum Depth of Binary Tree题解和总结
//1、最大值宏定义
#include <climits>
int max=INT_MAX;//Maximum value for an object of type int  32767 (2^15-1) or greater
//2、递归
int minDepth(TreeNode* root) {
        if(root==NULL) return 0;
        else if(root->right==NULL) return minDepth(root->left)+1;
        else if(root->left==NULL) return minDepth(root->right)+1;
        else return min(minDepth(root->left),minDepth(root->right))+1;
|
//另一解法
    int minDepth(TreeNode *root) {
        if (root == nullptr) {
            return 0;
        }

        if (root->left == nullptr && root->right == nullptr) {
            return 1;
        }
//如果非空且非叶节点，递归求子节点最小高度，然后加
        int min_depth = INT_MAX;
        if (root->left != nullptr) {
            min_depth = min(minDepth(root->left), min_depth);
        }
        if (root->right != nullptr) {
            min_depth = min(minDepth(root->right), min_depth);
        }
//该结点和节点子节点高度和
        return min_depth + 1;
}

```





