# Leetcode 22 括号生成
总的思路就是利用递归，如果左右两边都为0了，则添加当前结果，如果左边大于0，无脑加左边，如果右边比左边多，赶紧加右边，right>left 这个判断里就默认了right >0，但right>left的判断优先级更高。
```python
class Solution(object):
    
        
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        res = [];
        def generate( left, right, cur):
            if left==0 and right==0:
                res.append(cur);
            if left>0:
                generate( left-1, right, cur+"(");
            if right>left:
                generate( left, right-1, cur+")");
        generate( n, n, "");
        return res;
```
