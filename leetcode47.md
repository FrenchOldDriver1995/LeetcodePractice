重点理解sort排序之后，加一句和上一个元素比较，并且上一个元素已经使用过，则判定为重复
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
        for(int i=0; i<len; i++){
            if(used[i]) continue;
            if(i>0 && nums[i]==nums[i-1] && used[i-1]!=0) continue; //用排序的方式，只要和上一个一样并且上一个被用过了，就表明重复，但如果两个一样，但并没有使用，则可以
            ans.push_back(nums[i]);
            used[i] = 1;//尝试这个位置

            dfs(nums, used);
            ans.pop_back();//g归位
            used[i]=0;

        }
    }
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        len = nums.size();
        sort(nums.begin(), nums.end());
        used.assign(len, 0); //初始化状态数组
        dfs(nums, used);
        return ret;
    }
};
```
