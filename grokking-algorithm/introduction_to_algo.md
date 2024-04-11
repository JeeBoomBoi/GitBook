# Introduction to Algorithms

## Binary Search

Binary search works only if the input array is sorted and the run time is in O(log)

{% tabs %}
{% tab title="Java" %}
```text
class Solution {
    int binarysearch(int arr[], int n, int k) {
        // code here
        int low = 0;
        int high = n - 1;
        while(low <= high) {
            int mid = (low + high) / 2;
            int guess = arr[mid];
            if (guess == k) {
                return mid;
            } else if (guess > k) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return -1;
    }
}
```
{% endtab %}