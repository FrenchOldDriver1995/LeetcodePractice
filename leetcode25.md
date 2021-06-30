# Leetcode 25 k个一组反转链表
基本思路是先实现k个反转，再把最后不足k却被反转的那一段的头节点记录下来，最后单独从这个被记录的地方再反转一次。

start -> p -> q -> r -> *

start -> p <- q, r -> * 

start -> * <- p ,q-> r (count+1)

start -> * <- * <-p, q ->r(count+2)


当达到k之后，start之后那个标记为end，end接q， start之后应该接p，
这个时候start依旧连着原来的第一个节点（调整顺序后会变成尾节点）

跳出（内层）循环之后，

start -> 'end <- * <-p', q

start -> 'p -> * -> end' -> q

把中间那段翻顺序

然后要把start也更新

到最后的时候，假如还没到k，链表就到头了，需要把那段已经反转的又转回去, 只需要简单的记录这里开始的节点

start -> 'end <- * <-p' 

start -> 'p -> * - > *'

代码：
```python
class Solution(object):
    def reverseKGroup(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        
        if head.next==None or k==1:
            return head
        
        fake = ListNode(-1)
        fake.next = head
        start = fake
        p = head
        q = head.next
        flag=False
        while q:
            count = 1 
            while q: 
                
                    

                r = q.next #先记录后面的，
                q.next = p
                p = q
                q = r
                count+=1
                if count==k:
                    break
                if q==None and count<k:
                    #没到k就结束了，不反转
                    flag = True #设个Flag
                    reverseAgain = start #记录从哪里开始
                    
            end = start.next
            start.next = p
            end.next = q
            start = end
            p = start.next
            if p:
                q = p.next

        if flag:
            
            p =reverseAgain
            q = p.next
            while q.next:
                r = q.next 
                q.next = r.next
                r.next = p.next
                p.next = r
            
        return fake.next
```
