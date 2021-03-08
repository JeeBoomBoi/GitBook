# Day 3



**5\) Kadane’s Algorithm** 

[**https://www.youtube.com/watch?v=w\_KEocd\_\_20&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=5**](https://www.youtube.com/watch?v=w_KEocd__20&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=5) ****  


{% tabs %}
{% tab title="CPP" %}
```text
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int max_current = nums[0];
        int max_global = nums[0];
        for (int i = 1; i < nums.size(); i++)
        {
            max_current = max(nums[i], max_current + nums[i]);
            if (max_current > max_global)
            {
                max_global = max_current;
            }
        }
        return max_global;
    }
};
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

**6\) Merge Overlapping Subintervals**

[**https://www.youtube.com/watch?v=2JzRBPFYbKE&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=6**](https://www.youtube.com/watch?v=2JzRBPFYbKE&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=6)  


{% tabs %}
{% tab title="CPP" %}
```text
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        vector<vector<int>> result;
        sort(intervals.begin(), intervals.end());
        result.push_back(intervals[0]);
        for (int i = 1; i < intervals.size(); i++)
        {
            if (result.back()[1] >= intervals[i][0])
            {
                result.back()[1] = max(result.back()[1], intervals[i][1]);
            }
            else
            {
                result.push_back(intervals[i]);
            }
        }
        
        return result;
    }
};
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

**7\) Set Matrix Zeros** 

**\(**[**https://www.youtube.com/watch?v=M65xBewcqcI&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=7**](https://www.youtube.com/watch?v=M65xBewcqcI&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=7)**\)**   


{% tabs %}
{% tab title="CPP" %}
```text
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        vector<pair<int,int>> zeroplaces;
        int m = matrix.size();
        int n = matrix[0].size();
        for(int i = 0; i < m; i++)
        {
            for(int j = 0; j < n; j++)
            {
                if(matrix[i][j] == 0)
                {
                    zeroplaces.push_back(make_pair(i,j));
                }
            }
        }
        for (int i = 0; i < zeroplaces.size(); i++)
        {
            int x, y;
            x = zeroplaces[i].first;
            y = zeroplaces[i].second;
            for (int j = 0; j < m; j++)
            {
                matrix[j][y] = 0;
            }
            for (int j = 0; j < n; j++)
            {
                matrix[x][j] = 0;
            }
        }
    }
};
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

