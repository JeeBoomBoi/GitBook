# Sorting

## Bubble Sort
```cpp
#include <iostream>
using namespace std;

void bubbleSort(int arr[], int n)
{
    // Your code here  
    bool swapped = false;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j+1]);
                swapped = true;
            }
        }
        if (swapped == false)
            break;
    }
}

int main() {
	int arr[] = {34, 32, 56, 71, 18, 30, 20};
	int n = sizeof(arr) / sizeof(int);
	bubbleSort(arr, n);
	for (auto x : arr) {
	    cout << x << " ";
	}
	return 0;
}
```

## Selection sort
```cpp
#include <iostream>
using namespace std;

void selectionSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int min_index = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[min_index])
                min_index = j;
        }
        swap(arr[i], arr[min_index]);
    }
}

int main() {
	int arr[] = {34, 32, 56, 71, 18, 30, 20};
	int n = sizeof(arr) / sizeof(int);
	selectionSort(arr, n);
	for (auto x : arr) {
	    cout << x << " ";
	}
	return 0;
}
```

## Insertion Sort
```cpp
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}

int main() {
	int arr[] = {34, 32, 56, 71, 18, 30, 20};
	int n = sizeof(arr) / sizeof(int);
	insertionSort(arr, n);
	for (auto x : arr) {
	    cout << x << " ";
	}
	return 0;
}
```