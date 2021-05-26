# Searching

### 26/5/2021

## Binary Search
```
#include<bits/stdc++.h>
using namespace std;

int binarySearch(int *arr, int n, int k)
{
    int low = 0;
    int high = n - 1;
    while (low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] == k)
            return mid;
        else if (arr[mid] > k)
            high = mid - 1;
        else
            low = mid + 1;
    }
    return -1;
}

int recursivebinarySearch(int *arr, int low, int high, int k)
{
    if (low > high)
        return -1;
    int mid = (low + high) / 2;
    if (arr[mid] == k)
        return mid;
    else if (arr[mid] > k)
        return recursivebinarySearch(arr, low, mid - 1, k);
    else
        return recursivebinarySearch(arr, mid + 1, high, k);
}


int main()
{
    int arr[] = {1,2,3,4,5,6};
    int size = 6;
    int search = 5;
    cout << binarySearch(arr, size, search) << endl;
}
```

## First Occurence
```
#include<bits/stdc++.h>
using namespace std;

// recursive
int firstOccurence(int *arr, int low, int high, int x)
{
    if (low > high)
        return -1;
    int mid = (low + high) / 2;
    if (arr[mid] > x)
        return firstOccurence(arr, low, mid - 1, x);
    else if (arr[mid] < x)
        return firstOccurence(arr, mid + 1, high, x);
    else
    {
        if (mid == 0 || arr[mid - 1] != arr[mid])
            return mid;
        else
            return firstOccurence(arr, low, mid - 1, x);
    }
}

// iterative
int firstOccurence(int *arr, int n, int x)
{
    int low = 0;
    int high = n - 1;
    while(low <= high)
    {
        int mid = (low + high) / 2;
        if (arr[mid] > x)
            high = mid - 1;
        else if (arr[mid] < x)
            low = mid + 1;
        else
        {
            if (mid == 0 || arr[mid] != arr[mid - 1])
                return mid;
            else
                high = mid - 1;
        }
    }
    return -1;
}

int main()
{
    int arr[] = {1, 5, 5, 10, 10, 10, 20, 20, 30};
    cout << firstOccurence(arr, 0, 8, 10) << endl;
}
```
