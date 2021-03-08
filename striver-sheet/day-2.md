# Day 2



1. **Find the duplicate in an array of N+1 integers. \(Ignore the video quality, as this was the first video which i recorded\)** [**https://www.youtube.com/watch?v=32Ll35mhWg0&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=1**](https://www.youtube.com/watch?v=32Ll35mhWg0&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=1)  **\(Problem link in description\)**

**LeetCode 287.** [**https://leetcode.com/problems/find-the-duplicate-number/**](https://leetcode.com/problems/find-the-duplicate-number/)\*\*\*\*

\*\*\*\*

{% tabs %}
{% tab title="Python" %}
```text
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        dic = {}
        for num in nums:
            if num in dic:
                return dic[num]
            else:
                dic[num] = num
        
```
{% endtab %}

{% tab title="CPP" %}
```text
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        unordered_map<int, int> hm;
        for(int i = 0; i < nums.size(); i++) 
        {
            if(hm.find(nums[i]) != hm.end())
            {
                return hm[nums[i]];
            }
            hm[nums[i]] = nums[i];
        }
        return 0;
    }
};
```
{% endtab %}
{% endtabs %}



 **2.Sort an array of 0’s 1’s 2’s without using extra space or sorting algo** 

[**https://www.youtube.com/watch?v=oaVa-9wmpns&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=2**](https://www.youtube.com/watch?v=oaVa-9wmpns&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=2) **\(Problem link in description\)**

75. Sort Colors - [https://leetcode.com/problems/sort-colors/](https://leetcode.com/problems/sort-colors/)

{% tabs %}
{% tab title="Python" %}
```text
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        # Dutch Partioning Problem
        cnt0, cnt1, cnt2 = 0, 0, len(nums) - 1
        while cnt1 <= cnt2:
            if nums[cnt1] == 0:
                nums[cnt0], nums[cnt1] = nums[cnt1], nums[cnt0]
                cnt0 += 1
                cnt1 += 1
            elif nums[cnt1] == 1:
                cnt1 += 1
            else:
                nums[cnt1], nums[cnt2] = nums[cnt2], nums[cnt1]
                cnt2 -= 1
```
{% endtab %}

{% tab title="CPP" %}
```text
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int n0=count(nums.begin(),nums.end(),0);
        int n1=count(nums.begin(),nums.end(),1);
        int n2=count(nums.begin(),nums.end(),2);
        nums.clear();
        for(int i=0;i<n0;i++)
        {
            nums.push_back(0);
        }
        
        for(int i=0;i<n1;i++)
        {
            nums.push_back(1);
        }
        
        for(int i=0;i<n2;i++)
        {
            nums.push_back(2);
        }
    }
};
```
{% endtab %}
{% endtabs %}





**3. Repeat and Missing Number** 

[**https://www.youtube.com/watch?v=5nMGY4VUoRY&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=3**](https://www.youtube.com/watch?v=5nMGY4VUoRY&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=3)  **\(Problem link in description\)**

**286. Missing Number -** [**https://leetcode.com/problems/missing-number/**](https://leetcode.com/problems/missing-number/)\*\*\*\*

{% tabs %}
{% tab title="Python" %}
```text
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        return n * (n+1) // 2 - sum(nums)
```
{% endtab %}

{% tab title="CPP" %}
```text
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int x1 = 0, x2 = 0;
        for (int i = 0; i < nums.size(); i++)
        {
            x1 = x1 ^ nums[i];
            x2 = x2 ^ (i+1);
        }
        return x1 ^ x2;
    }
};
```
{% endtab %}
{% endtabs %}

\*\*\*\*

**4. Merge two sorted Arrays without extra space** 

[**https://www.youtube.com/watch?v=hVl2b3bLzBw&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=4**](https://www.youtube.com/watch?v=hVl2b3bLzBw&list=PLgUwDviBIf0rPG3Ictpu74YWBQ1CaBkm2&index=4)  **\(Problem link in description\)**

88. Merge Sorted Array - [https://leetcode.com/problems/merge-sorted-array/](https://leetcode.com/problems/merge-sorted-array/)

{% tabs %}
{% tab title="CPP" %}
```text
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;
        
        while(i >= 0 && j >= 0)
        {
            if(nums1[i] > nums2[j])
            {
                nums1[k--] = nums1[i--];
            }
            else
            {
                nums1[k--] = nums2[j--]; 
            }
        }
        
        while(j >= 0)
        {
            nums1[k--] = nums2[j--];
        }
    }
};
```
{% endtab %}

{% tab title="Python" %}
```text
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        while m > 0 and n > 0:
            if nums1[m - 1] > nums2[n - 1]:
                nums1[m + n - 1] = nums1[m - 1]
                m -= 1
            else:
                nums1[m + n - 1] = nums2[n - 1]
                n -= 1
                
        nums1[:n] = nums2[:n]
```
{% endtab %}
{% endtabs %}



