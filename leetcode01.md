开始练习用C/C++刷题\
注意C++中的vector类似java的List，他的大小是.size()

```C
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        
        for(int i=0; i<nums.size(); i++){
            for(int j=i+1; j<nums.size(); j++){
                if (nums[i]+nums[j]==target){
                    return {i, j};
                }
            }
        }
        return {};
    }
};
```
