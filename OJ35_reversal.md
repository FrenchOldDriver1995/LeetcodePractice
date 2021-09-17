字符串相关的模板题，建议熟练掌握，遇到一连串字符串，用vector先存折，然后循环，对立面的每一个string，他其实也是可以直接循环的

类似题目也是同理，大模板都可以套这个

```C
#include<vector>
#include<iostream>
using namespace std;
int main()
{  

    vector<string> strs;
    string s;
    while(cin>>s){
        strs.push_back(s);
    }
    
    for(int i=0; i<strs.size(); i++){
        string cur = strs[i];
        for(int j=cur.length()-1; j>=0; j--)cout<<cur[j];
        if(i<strs.size()-1)cout<<" ";
    }
  return 0;
}
```
