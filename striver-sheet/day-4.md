# Day 4



**1\) Set Matrix Zeros** 

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

2\) **Pascal Triangle** 

[**https://www.youtube.com/watch?v=6FLvhQjZqvM&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=8**](https://www.youtube.com/watch?v=6FLvhQjZqvM&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=8)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> result;
        int num = 1;
        for (int i = 0; i < numRows; i++)
        {
            vector<int> temp;
            for (int j = 0; j <= i; j++)
            {
                if (j == 0 || j == i)
                {
                    temp.push_back(1);
                }
                else
                {
                    temp.push_back(result[i-1][j-1] + result[i-1][j]);
                }
            }
            result.push_back(temp);
        }
        return result;
    }
};
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

3\) **Next Permutation \(Personally, found this hard to understand\)** 

[**https://www.youtube.com/watch?v=LuLCLgMElus&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=9**](https://www.youtube.com/watch?v=LuLCLgMElus&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=9)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        int n = nums.size(), k, l;
    	for (k = n - 2; k >= 0; k--) {
            if (nums[k] < nums[k + 1]) {
                break;
            }
        }
    	if (k < 0) {
    	    reverse(nums.begin(), nums.end());
    	} else {
    	    for (l = n - 1; l > k; l--) {
                if (nums[l] > nums[k]) {
                    break;
                }
            } 
    	    swap(nums[k], nums[l]);
    	    reverse(nums.begin() + k + 1, nums.end());
        }
    }
};
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

