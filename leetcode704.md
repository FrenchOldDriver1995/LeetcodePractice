704 二分查找，熟悉C++的语言操作，其实大部分写法跟java差不多。注意判断里面要写else if，
```C
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int L = 0;
        int R = nums.size()-1;
        while (L<=R){
            int mid = L+(R-L)/2;
            if (nums[mid]<target)L=mid+1;
            else if (nums[mid]>target) R = mid-1; //这里要写else if
            else return mid;
        }
        return -1;
    }
};
```
