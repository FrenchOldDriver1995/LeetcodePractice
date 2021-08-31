熟悉代码，效率不是很高
注意C++中Node的声明要加*
空值是NULL, 类型中的属性用->表示
```
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* root = new ListNode(0);
        ListNode* cursor = root;
        vector<int> res;
        int add=0;
        while (l1!=NULL || l2!=NULL || add!=0){
            int l1val = l1==NULL? 0 : l1->val;
            int l2val = l2==NULL? 0 : l2->val;
            int sumVal = l1val + l2val +add;
            add = sumVal/10;

            ListNode* sumNode = new ListNode(sumVal % 10); //每次把当前结果存进新的node
            cursor->next = sumNode; //连接假头节点，方便最后的返回结果
            cursor = sumNode; // update

            if (l1!=NULL)l1 = l1->next;
            if(l2!=NULL)l2 = l2->next;
            
        }

        return root->next;
    }
};
```
