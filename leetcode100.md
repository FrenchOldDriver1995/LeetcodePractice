两颗相同的树, 递归解法是最简单的，即当前节点值相同 && 左子树相同 && 右子树相同
```C
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(!p && !q)return true;      
        if(p && q){
        return p->val==q->val&&isSameTree(p->left,q->left)&&isSameTree(p->right,q->right);
        }else return false;
    }
};
```
