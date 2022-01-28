# COIN_CHANGE_2_DP-
Code :: c++
#include<bits/stdc++.h>
using namespace std;
int DP(int coin[],int n,int W){
    int t[n+1][W+1];
    for(int i=0;i<n+1;i++){
        for(int j=0;j<W+1;j++){
            if(i==0){
                t[i][j]=INT_MAX -1;
            }
            if(j==0){
                t[i][j]=0;
            }
        }
    }
   for(int i=1;i<2;i++){
   for(int j=2;j<W+1;j++){
       if(j%coin[0]==0){
       t[i][j]=j/coin[0];
       }
       else{
           t[i][j]=INT_MAX-1;
       }
   }
   }

 for(int i=2;i<n+1;i++){
        for(int j=1;j<W+1;j++){
            if(coin[i-1]<=j)
            {
                t[i][j]=min(1+t[i][j-coin[i-1]],t[i-1][j]);
            }
            else{
                t[i][j]=t[i-1][j];
            }
        }
    }

return t[n][W];
}

int main(){
    int n,W;
    cout<<"enter weight "<<endl;
    cin>>W;
    cout<<"enter size of array";
    cin>>n;
    int coin[n];
    cout<<"enter array elements";
    for(int i=0;i<n;i++){
        cin>>coin[i];
    }
    cout<<DP(coin,n,W);
    return 0;    
}
