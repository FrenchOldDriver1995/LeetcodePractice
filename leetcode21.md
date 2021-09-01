合并两个有序链表，除开递归，重要是熟悉指针法，只用一个指针即可，不需要两个，当然两个也可以
```C
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* fake = new ListNode(0);
        ListNode* cur = fake; //移动点， 记录点
        if (!l1 && !l2)return l1;
        if (!l1 && l2)return l2;
        if (l1 && !l2)return l1;
        
        while (l1 && l2){
            if(l1->val < l2->val){
                cur->next = l1;
                cur = cur->next;
                l1 = l1->next;
            }else{
                cur->next = l2;
                cur = cur->next;
                l2 = l2->next;
            }
        }
        if(!l1)cur->next = l2;
        else cur->next = l1;

        return fake->next;
    }
};
```
