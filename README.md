#include <bits/stdc++.h>
using namespace std;

 // } Driver Code Ends
class Solution {
  public:
    int editDistance(string s1, string s2) {
        // Code here
        int m=s1.size();
    int n=s2.size();
    int **output=new int*[m+1];
    for(int i=0;i<m+1;i++)
    {
        output[i]=new int[n+1];
    }
    
    output[0][0]=0;
    
    for(int j=1;j<n+1;j++)
    {
        output[0][j]=j;
    }
    
    for(int i=1;i<m+1;i++)
    {
        output[i][0]=i;
    }
    
    for(int i=1;i<m+1;i++)
    {
        for(int j=1;j<n+1;j++)
        {
            if(s1[m-i]==s2[n-j])
            {
                output[i][j]=output[i-1][j-1];
            }
            else
            {
                int a=output[i-1][j];
                int b=output[i][j-1];
                int c=output[i-1][j-1];
                
                output[i][j]=min(a,min(b,c))+1;
            }
        }
    }
       return output[m][n];  
    }
};

// { Driver Code Starts.
int main() {
    int T;
    cin >> T;
    while (T--) {
        string s, t;
        cin >> s >> t;
        Solution ob;
        int ans = ob.editDistance(s, t);
        cout << ans << "\n";
    }
    return 0;
}

