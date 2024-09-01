_Suggestions and Constructive criticism are welcome_

**Problem** : _Binary Tree Level Order Traversal_
_Given root of a binary tree. You have to return list of each levels._

**Approach** :

We push root node to a queue `q`. So, currently level `0` is in the `q`.

Now we take the size of `q`, let it be `n` (If I frame this sentence in another way, n is the size of level 0), and run a loop `n` times. 

What has happened here? here we achieved an **isolated loop** where **only the members of a particular level could be popped**. Right? 
            
_Now there can be multiple approaches to get the level order traversal. I am proposing one :_

while looping, when we pop a node out of `q`, we get the value of that node and push it to a vector `levelArray`.  Push the node's left and right child to `q`. Since we are running the loop for current level, the ones being pushed to `q` will not be popped inside our current loop. Also by this step, we are evidently pushing the members of the next level, which we are going to start over again after the current loop is over.
 
Okay. So how to get each levels now? 
by our previous explained approach, we are confident that q contains a single level always outside loop. So just put a condition `while(!q.empty())` outside all the gibberish things above, and in the end of the while loop, push the vector `levelArray` to the answer. Thats it.

```
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {

        vector<vector<int>> ans;

        // if node is empty, return
        if(root == NULL)return ans; 

        queue<TreeNode*>q; 
        q.push(root); 
             
        while(!q.empty()) {

            // each level is going to be explored here
            int size = q.size(); // size of current level
            vector<int>levelArray;

            for(int i = 0; i < size; i++) {
                // current node
                TreeNode *node = q.front(); 
                q.pop(); 

                // push the value into the levelArray. 
                levelArray.push_back(node->val); 

                // push children to q
                if(node->left != NULL)q.push(node->left); 
                if(node->right != NULL)q.push(node->right); 
            }

            // level array now has all required elements.
            ans.push_back(levelArray);
        }

        return ans;
    }
};
```

Okay. I think conceptually _level order traversal_ and _breadth first search_ are same once you avoid getting each level seperate.
