/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    // Helper function to calculate the height of the tree and check if it is balanced
    int height(TreeNode* root) {
        if (root == nullptr) {
            return 0;
        }
        int leftHeight = height(root->left);
        int rightHeight = height(root->right);
        
        // If left or right subtree is unbalanced, return -1 to indicate imbalance
        if (leftHeight == -1 || rightHeight == -1 || abs(leftHeight - rightHeight) > 1) {
            return -1; 
        }
        
        // Return the height of the tree at the current node
        return max(leftHeight, rightHeight) + 1;
    }

    // Main function that checks if the tree is balanced
    bool isBalanced(TreeNode* root) {
        return height(root) != -1;
    }
};
