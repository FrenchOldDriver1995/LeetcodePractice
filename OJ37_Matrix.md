模板题，熟悉DP以及C++相应写法，感觉C++写起来比较顺手，他的数组只需要int name[N][M]就行了，默认数组就全是0了，不需要像java那样还要new int[N][M](这个反倒C++不行).

然后两层for循环还能写的再简单点，直接不要大括号然后全部写一行
```C
int main()
{  
  // please define the C++ input here. For example: int a,b; cin>>a>>b;;  
  // please finish the function body here.  
  // please define the C++ output here. For example:cout<<____<<endl; 
    int N, M;
    cin>>N>>M;
    int vec[N][M];
    for (int i=0; i<N; i++){
        for (int j=0; j< M; j++){
            cin>>vec[i][j];
        }
    }
    
    int dp[N][M];
    dp[0][0]=vec[0][0];
    for(int i=1; i<N; i++)dp[i][0]=dp[i-1][0]+vec[i][0];
    for(int j=1; j<M; j++)dp[0][j]=dp[0][j-1]+vec[0][j];
    
    
    for (int i=1; i<N; i++){
        
        for (int j=1; j<M; j++){

            dp[i][j] = max(dp[i-1][j], dp[i][j-1]) + vec[i][j];

        }
        
    }
    cout<<dp[N-1][M-1];
  return 0;
}
```
