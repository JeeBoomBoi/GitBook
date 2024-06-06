# Two Pointers

## 125. Valid Palindrome
link - [https://leetcode.com/problems/valid-palindrome/description/](https://leetcode.com/problems/valid-palindrome/description/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public boolean isPalindrome(String s) {
        int i = 0;
        int j = s.length() - 1;
        while (i < j) {
            char a = s.charAt(i);
            char b = s.charAt(j);
            if (!Character.isLetterOrDigit(a)) {
                i++;
                continue;
            }

            if (!Character.isLetterOrDigit(b)) {
                j--;
                continue;
            }

            if (Character.toLowerCase(a) != Character.toLowerCase(b)) {
                return false;
            }

            i++;
            j--;
        }
        return true;
    }
}
```
{% endtab %}
{% endtabs %}

## 167. Two Sum II - Input Array Is Sorted
link - [https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int i = 0;
        int length = numbers.length;
        int j = length - 1;
        while (i < length - 1 && j > i) {
            if (numbers[i] + numbers[j] == target) {
                return new int[]{i + 1, j + 1};
            } 
            if (numbers[i] + numbers[j] < target) {
                i++;
            } else {
                j--;
            }     
        }
        return new int[]{};
    }
}
```
{% endtab %}
{% endtabs %}

## 15. 3Sum
link - [https://leetcode.com/problems/3sum/](https://leetcode.com/problems/3sum/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> sol = new ArrayList();
        Arrays.sort(nums);

        for (int i = 0; i < nums.length - 2; i++) {
            if (i == 0 || (i > 0 && nums[i] != nums[i - 1])) {
                int target = 0 - nums[i];
                int left = i + 1;
                int right = nums.length - 1;

                while (left < right) {
                    List<Integer> miniSol = new ArrayList();
                    if (nums[left] + nums[right] == target) {
                        miniSol.add(nums[i]);
                        miniSol.add(nums[left]);
                        miniSol.add(nums[right]);
                        sol.add(miniSol);
                        while (left < right && nums[left] == nums[left + 1]) {
                            left++;
                        }
                        while (left < right && nums [right] == nums[right - 1]) {
                            right--;
                        }
                        left++;
                        right--;
                    }
                    else if (nums[left] + nums[right] < target) {
                        left++;
                    } else {
                        right--;
                    }
                }
            }
        }

        return sol;
    }
}
```
{% endtab %}
{% endtabs %}

## 11. Container With Most Water
link - [https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int maxArea(int[] height) {
        int area = 0;
        int left = 0;
        int right = height.length - 1;

        while (left < right) {
            area = Math.max(Math.min(height[left], height[right]) * (right - left), area);
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }
        return area;
    }
}
```
{% endtab %}
{% endtabs %}


## 42. Trapping Rain Water
link - [https://leetcode.com/problems/trapping-rain-water/](https://leetcode.com/problems/trapping-rain-water/)

{% tabs %}
{% tab title="Java" %}
```java
class Solution {
    public int trap(int[] height) {
        int n = height.length;
        int l = 0;
        int r = n - 1;
        int leftMax = height[0];
        int rightMax = height[n - 1];
        int c = 0;

        while (l < r) {
            if (leftMax < rightMax) {
                l++;
                leftMax = Math.max(height[l], leftMax);
                c += leftMax - height[l];
            } else {
                r--;
                rightMax = Math.max(height[r], rightMax);
                c += rightMax - height[r];
            }
        }

        return c;
    }
}
```
{% endtab %}
{% endtabs %}
