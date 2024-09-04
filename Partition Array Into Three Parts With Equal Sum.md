```cpp
class Solution {
public:
    bool canThreePartsEqualSum(vector<int>& arr) {
        //Aryan 169 Series
        /*
            - running sum = s
            - s/2 occured before and suffix sum is also s/2
        */

        int n = arr.size();
        int suffix[n];
        suffix[n-1] = arr[n-1];
        for(int i=n-2;i>=0;i--){
            suffix[i] = suffix[i+1] + arr[i];
        }

        int running_sum = 0;
        unordered_map<int,int> mpp;

        for(int i=0;i<n;i++){
            running_sum += arr[i];
            if(i>0 && i<n-1 && running_sum % 2 ==0  && mpp.find(running_sum/2) != mpp.end() && suffix[i]-arr[i] == running_sum/2){
                return true;
            }

            mpp[running_sum]++;
        }
        return false;
    }
};
```
