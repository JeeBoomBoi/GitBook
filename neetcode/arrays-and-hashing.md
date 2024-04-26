# Arrays and Hashing

## 217. Contains Duplicate
link - [https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> hashSet = new HashSet();
        for (int x: nums) {
            if (hashSet.contains(x)) {
                return true;
            }
            hashSet.add(x);
        }
        return false;
    }
}
```
{% endtab %}

{% tab title="Python" %}
```py
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        my_set = set()
        for i in nums:
            if i in my_set:
                return True
            my_set.add(i)
        return False
```
{% endtab %}
{% endtabs %}

## 242. Valid Anagram
link - [https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)

{% tabs %}
{% tab title="Java Initial Approach" %}
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        HashMap<Character, Integer> hashMap = new HashMap();
        for (int i = 0; i < s.length(); i++) {
            char a = s.charAt(i);
            int x = hashMap.getOrDefault(s.charAt(i), 0);
            hashMap.put(a, ++x);
        }
        for (int i = 0; i < t.length(); i++) {
            char b = t.charAt(i);
            if (!hashMap.containsKey(b)) {
                return false;
            } else {
                hashMap.put(b, hashMap.get(b) - 1);
                if (hashMap.get(b) < 0) {
                    return false;
                }
            }
        }
        return true;
    }
}
```
{% endtab %}

{% tab title="Java Optimal Approach" %}
```java
class Solution {
    // will only work if characters are a-z
    public boolean isAnagram(String s, String t) {
        int[] alphabet = new int[26];
        for (int i = 0; i < s.length(); i++) {
            alphabet[s.charAt(i) - 'a']++;
        }
        for (int i = 0; i < t.length(); i++) {
            alphabet[t.charAt(i) - 'a']--;
        }
        for (int i : alphabet) {
            if (i != 0) {
                return false;
            }
        }
        return true;
    }
}
```
{% endtab %}

{% tab title="Python" %}
```py
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # check the length of strings
        # if not return false
        if len(s) != len(t):
            return False
        
        # dictionary will hold the count of each character in string s
        my_dict = {}
        for i in s:
            if i not in my_dict:
                my_dict[i] = 1
            else:
                my_dict[i] += 1
        
        for i in t:
            # check if the character in string t exist in dictionary 
            if i not in my_dict:
                return False
            # reduce count of element in dictionary
            my_dict[i] -= 1
            # check if the count is less than 0
            if my_dict[i] < 0:
                return False

        return True
```
{% endtab %}
{% endtabs %}

## 1. Two Sum

link - [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)
{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] arr = new int[2];
        HashMap<Integer, Integer> hashMap = new HashMap();
        for (int i = 0; i < nums.length; i++) {
            int x = target - nums[i];
            if (hashMap.containsKey(nums[i])) {
                arr[0] = hashMap.get(nums[i]);
                arr[1] = i;
                return arr;
            }
            hashMap.put(x, i);
        }
        return arr;
    }
}
```
{% endtab %}

{% tab title="Python" %}
```py
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # declare a dictionary which will contain
        # the number and the index
        my_dict = {}

        for i in range(0, len(nums)):
            # storing remainder from target 
            num = target - nums[i]
            
            # checking if the remainder is already present in the dictionary
            # if the number is present return the current index and the index of stored number 
            if num in my_dict:
                return {i, my_dict[num]}
            
            # store the current number along with the index
            my_dict[nums[i]] = i
```
{% endtab %}
{% endtabs %}

## 49. Group Anagrams
link - [https://leetcode.com/problems/group-anagrams/](https://leetcode.com/problems/group-anagrams/)
{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map <List<Integer>, List<String>> hashMap = new HashMap();
        for (String s : strs) {
            int[] arr = new int[26];
            for (int i = 0; i < s.length(); i++) {
                arr[s.charAt(i) - 'a']++;
            }
            ArrayList<Integer> list = new ArrayList();
            for (int a : arr) {
                list.add(a);
            }
            if (hashMap.containsKey(list)) {
                hashMap.get(list).add(s);
            } else {
                ArrayList<String> stringList = new ArrayList();
                stringList.add(s);
                hashMap.put(list, stringList);
            }
        }
        return new ArrayList<>(hashMap.values());
    }
}
```
{% endtab %}

{% tab title="Java Optimal Approach" %}
```java
public List<List<String>> groupAnagrams(String[] strs) {
    if (strs == null || strs.length == 0) return new ArrayList<>();
    Map<String, List<String>> map = new HashMap<>();
    for (String s : strs) {
        char[] ca = new char[26];
        for (char c : s.toCharArray()) ca[c - 'a']++;
        String keyStr = String.valueOf(ca);
        if (!map.containsKey(keyStr)) map.put(keyStr, new ArrayList<>());
        map.get(keyStr).add(s);
    }
    return new ArrayList<>(map.values());
}
```
{% endtab %}

{% tab title="Python" %}
```py
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        # define a default dictionary
        # doesn't throw a key error when value doesn't exist
        my_dict = defaultdict(list)

        # iterate over all the strings
        for s in strs:
            # create a list of size 26
            li = [0] * 26
            # loop over each character in a string
            for c in s:
                # add 1 to the index of each character
                li[ord(c) - ord('a')] += 1
            # add the result to the dictionary => (tuple, string)
            my_dict[tuple(li)].append(s)

        # return the values of dictionary 
        return my_dict.values()
```
{% endtab %}
{% endtabs %}

## 347. Top K Frequent Elements
link - [https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)

* The heap is one maximally efficient implementation of an abstract data type called a priority queue, and in fact, priority queues are often referred to as "heaps", regardless of how they may be implemented. In a heap, the highest (or lowest) priority element is always stored at the root. However, a heap is not a sorted structure; it can be regarded as being partially ordered. A heap is a useful data structure when it is necessary to repeatedly remove the object with the highest (or lowest) priority, or when insertions need to be interspersed with removals of the root node.

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        if (k == nums.length) {
            return nums;
        }
        
        Map<Integer, Integer> hashMap = new HashMap();
        for (int n : nums) {
            hashMap.put(n, hashMap.getOrDefault(n, 0) + 1);
        } 

        Queue<Integer> heap = new PriorityQueue<>(
            // Lambda expression 
            // Comparator to store the least frequent first
            (n1, n2) -> hashMap.get(n1) - hashMap.get(n2));

        for (int n : hashMap.keySet()) {
            heap.add(n);
            if (heap.size() > k) {
                System.out.println(heap);
                heap.poll();
            }    
        }

        int[] top = new int[k];
        for (int i = k - 1; i >= 0; i--) {
            top[i] = heap.poll();
        }
        return top;
        
    }
}
```
{% endtab %}
{% tab title="Python" %}
```py
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        # dictionary to store the counts 
        count = {}
        # array of array to store the frequency of counts
        freq = [[] for i in range(len(nums) + 1)]

        # populating the dictionary with number and count
        for i in nums:
            count[i] = 1 + count.get(i, 0)
        # populating the frequency array (freq -> digit)
        for n, c in count.items():
            freq[c].append(n)

        # creating a result array
        res = []
        # traversing from the back of frequency array to get the most frequent element
        for i in range(len(freq) - 1, 0, -1):
            # traversing the array corresponding to the count
            for j in freq[i]:
                # Adding the number to the result array
                res.append(j)
                # if count is equal to the k most frequent, return result
                if (len(res) == k):
                    return res
```
{% endtab %}
{% endtabs %}
