<font size = 6, color=red> Analysis of algorithms </font>
- theoretical study of computer-program performance and resource usage
- performance often draws the line between what is ***feasible*** and what is ***impossible***
- everything within this course is LOG base 2 due to hardware bit requirements
- We analyze algorithms based off Time, Space (memory etc) 
<font size =6> Asymptotic Performance</font> 
- worst case provides an upper bound in the running time
- average case gives us an estimate of the expected running time



![[Pasted image 20240908163619.png]]

**Average-Case**
![[Pasted image 20240908161128.png]]
- Complexity scales up as it gets more advances
- we look at growth of T(n) of an algorithm as n goes to infinity
![[Pasted image 20240908165727.png]]

<font size = 6> Insertion Sort Vs Merge Sort</font> 

- **Insertion Sort** n^2 run time
- **Merge sort** nlg(n) run time

Merge sort is a divide and conquer sorting algorithm it recursively splits the array into smaller subarrays and sortts each one before merging them back 
1. **Divide the array**
	- Split the array into two halfs
	- Recursively divide each half until each subarray contains only one element
2. **Merge the subarrays**
	- Merge subarrays back in sorted order
	- while merging compare elements of both subarrays and place the smaller element into the result array first
3. **Repeat**
	- Repeat merge until all subarray are merged back into a single sorted array

### Example:

Let’s sort the array `[38, 27, 43, 3, 9, 82, 10]` using merge sort.

1. **Divide**:
    - `[38, 27, 43, 3, 9, 82, 10]`
    - Split into `[38, 27, 43]` and `[3, 9, 82, 10]`
2. **Recursive Sorting**:
    
    - `[38, 27, 43]` splits into `[38]` and `[27, 43]`
    - `[27, 43]` splits into `[27]` and `[43]`
    - `[3, 9, 82, 10]` splits into `[3, 9]` and `[82, 10]`
    - Recursively split further until single-element arrays remain.
3. **Merge**:
    
    - Merge `[27]` and `[43]` to get `[27, 43]`
    - Merge `[38]` and `[27, 43]` to get `[27, 38, 43]`
    - Merge `[3, 9]` and `[10, 82]` to get `[3, 9, 10, 82]`
    - Finally, merge `[27, 38, 43]` and `[3, 9, 10, 82]` to get the sorted array: `[3, 9, 10, 27, 38, 43, 82]`
C++ Implementation 

```c++
#include <iostream>
using namespace std;

// Function to merge two subarrays into a sorted array
void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;  // Size of the left subarray
    int n2 = right - mid;     // Size of the right subarray

    // Temporary arrays to hold the values
    int leftArr[n1], rightArr[n2];

    // Copy data into temporary arrays
    for (int i = 0; i < n1; i++)
        leftArr[i] = arr[left + i];
    for (int i = 0; i < n2; i++)
        rightArr[i] = arr[mid + 1 + i];

    // Merge the temp arrays back into arr[left..right]
    int i = 0, j = 0, k = left;  // Initial indexes for leftArr, rightArr, and merged array
    while (i < n1 && j < n2) {
        if (leftArr[i] <= rightArr[j]) {
            arr[k] = leftArr[i];
            i++;
        } else {
            arr[k] = rightArr[j];
            j++;
        }
        k++;
    }

    // Copy the remaining elements of leftArr, if any
    while (i < n1) {
        arr[k] = leftArr[i];
        i++;
        k++;
    }

    // Copy the remaining elements of rightArr, if any
    while (j < n2) {
        arr[k] = rightArr[j];
        j++;
        k++;
    }
}

// Function to perform merge sort
void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        // Find the middle point
        int mid = left + (right - left) / 2;

        // Recursively sort both halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        // Merge the sorted halves
        merge(arr, left, mid, right);
    }
}

// Function to print an array
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        cout << arr[i] << " ";
    cout << endl;
} // void functions perform operations remember 

// Main function
int main() {
    int arr[] = {38, 27, 43, 3, 9, 82, 10};
    int arr_size = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: \n";
    printArray(arr, arr_size);

    mergeSort(arr, 0, arr_size - 1);

    cout << "Sorted array: \n";
    printArray(arr, arr_size);
    return 0;
}

```
![[Pasted image 20240908170733.png]]

<font size = 7, color = red> Insertion Sort</font> 
**Insertion Sort** is a simple, intuitive sorting algorithm that builds a sorted portion of the array one element at a time. It’s efficient for small or nearly sorted arrays, but less efficient for large or randomly sorted arrays. Here's how it works:

### Steps:

1. **Start with the First Element**:
    - Consider the first element as sorted.
2. **Pick the Next Element**:
    - Take the next element (from the unsorted portion of the array) and insert it into its correct position in the sorted portion.
3. **Shift Elements if Necessary**:
    - Shift elements of the sorted portion to the right until the correct position for the current element is found.
4. **Repeat**:
    - Continue the process for each element in the array until the entire array is sorted.
### Example:

Let’s sort the array `[12, 11, 13, 5, 6]` using Insertion Sort.

1. **First Pass**:  
    Sorted portion: `[12]`  
    Next element: `11`  
    Compare `11` with `12`, shift `12` to the right, and insert `11`:  
    Result: `[11, 12, 13, 5, 6]`
    
2. **Second Pass**:  
    Sorted portion: `[11, 12]`  
    Next element: `13`  
    No shift needed, `13` is already in place.  
    Result: `[11, 12, 13, 5, 6]`
    
3. **Third Pass**:  
    Sorted portion: `[11, 12, 13]`  
    Next element: `5`  
    Compare `5` with `13`, `12`, and `11`, shift them all to the right, and insert `5`:  
    Result: `[5, 11, 12, 13, 6]`
    
4. **Fourth Pass**:  
    Sorted portion: `[5, 11, 12, 13]`  
    Next element: `6`  
    Compare `6` with `13`, `12`, and `11`, shift `13` and `12` to the right, and insert `6`:  
    Final result: `[5, 6, 11, 12, 13]`

```c++
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];  // The current element to be inserted
        int j = i - 1;

        // Shift elements of arr[0..i-1] that are greater than key to one position ahead
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j = j - 1;
        }
        arr[j + 1] = key;  // Insert key at the correct position
    }
}

// Utility function to print the array
void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}

int main() {
    int arr[] = {12, 11, 13, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Original array: \n";
    printArray(arr, n);

    insertionSort(arr, n);

    cout << "Sorted array: \n";
    printArray(arr, n);

    return 0;
}

```

Note: Generally insertion sort is better on smaller data sets as it can out compete merge sort until catching up with the time complexity 
![[Pasted image 20240908171312.png]]
Writing and solving recurrence relations 
![[Pasted image 20240908171850.png]]
- Finding Upper Bound for time complexity that describes how it functions, knowing the recurrence for an algorithm we can find the given time complexity through various different methods one of those being the tree method 
