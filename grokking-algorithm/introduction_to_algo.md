# Introduction to Algorithms

## Binary Search

Binary search works only if the input array is sorted and the run time is in O(log n)

{% tabs %}
{% tab title="Java" %}
```java
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

## Common run times

* O(log n) - log time - Binary search
* O(n) - linear time - Simple search
* O(n log n) - Quicksort
* O(n<sup>2</sup>) - Selection sort
* O(n!) - Traveling salesman