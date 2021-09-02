全排列递归做法，在dfs函数的循环中，先改变状态再循环，然后状态归位。
```C
class Solution {
public:
    int len;
    vector<vector<int>> ret;
    vector<int> used;
    vector<int> ans;

    void dfs(vector<int>& nums, vector<int> used){
        if(ans.size()==len){
            ret.push_back(ans);
            return;
        }
        for(int i=0; i<len; ++i){
            if(used[i]) continue;
            ans.push_back(nums[i]);
            used[i] = 1;//尝试这个位置

            dfs(nums, used);
            ans.pop_back();//g归位
            used[i]=0;

        }
    }
    vector<vector<int>> permute(vector<int>& nums) {
        len = nums.size();
        used.assign(len, 0); //初始化状态数组
        dfs(nums, used);
        return ret;
    }
};
```
