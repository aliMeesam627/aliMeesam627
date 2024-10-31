Bubble Sort Code:
#include <iostream>
#include <chrono> // For timing the execution
using namespace std;
using namespace std::chrono;
int main() {
 int arr[] = {5, 45, 49, 11, 7};
 int n = sizeof(arr) / sizeof(arr[0]);
 // Start time
 auto start = high_resolution_clock::now();
 // Bubble Sort Algorithm
 for (int i = 0; i < n - 1; i++) {
 for (int j = 0; j < n - i - 1; j++) {
 if (arr[j] > arr[j + 1]) {
 // Swap arr[j] and arr[j + 1]
 int temp = arr[j];
 arr[j] = arr[j + 1];
 arr[j + 1] = temp;
 }
 }
 }
 // End time
 auto end = high_resolution_clock::now();

 // Calculate the duration of sorting
 auto duration = duration_cast<microseconds>(end - start);
 // Output the sorted array
 cout << "Sorted array: ";
 for (int i = 0; i < n; i++) {
 cout << arr[i] << " ";
 }
 cout << endl;
 // Print the execution time
 cout << "Execution time: " << duration.count() << " microseconds" << endl;
 return 0
}


Selection Sort Code:
#include <iostream>
#include <chrono> // For timing the execution
using namespace std;
using namespace std::chrono;
int main() {
 int arr[] = {5, 45, 49, 11, 7};
 int n = sizeof(arr) / sizeof(arr[0]);
 // Start time
 auto start = high_resolution_clock::now();
 // Bubble Sort Algorithm
 for (int i = 0; i < n - 1; i++) {
 bool swapped = false; // Optimization flag
 for (int j = 0; j < n - i - 1; j++) {
 if (arr[j] > arr[j + 1]) {
 // Swap arr[j] and arr[j + 1]
 int temp = arr[j];
 arr[j] = arr[j + 1];
 arr[j + 1] = temp;
 swapped = true; // A swap occurred
 }
 }
 // If no swaps occurred in this pass, array is already sorted
 if (!swapped) break;
 }
 // End time
 auto end = high_resolution_clock::now();

 // Calculate the duration of sorting
 auto duration = duration_cast<microseconds>(end - start);
 // Output the sorted array
 cout << "Sorted array: ";
 for (int i = 0; i < n; i++) {
 cout << arr[i] << " ";
 }
 cout << endl;
 // Print the execution time
 cout << "Execution time: " << duration.count() << " microseconds" << endl;
 return 0;
}



Merge Sort Code:
#include <iostream>
#include <chrono> // For timing the execution
using namespace std;
using namespace std::chrono;
// Function to merge two halves
void merge(int arr[], int left, int mid, int right) {
 int n1 = mid - left + 1; // Size of left subarray
 int n2 = right - mid; // Size of right subarray
 // Create temporary arrays
 int* L = new int[n1];
 int* R = new int[n2];
 // Copy data to temporary arrays
 for (int i = 0; i < n1; i++)
 L[i] = arr[left + i];
 for (int j = 0; j < n2; j++)
 R[j] = arr[mid + 1 + j];
 // Merge the temporary arrays back into arr[left..right]
 int i = 0; // Initial index of the first subarray
 int j = 0; // Initial index of the second subarray
 int k = left; // Initial index of merged subarray
 while (i < n1 && j < n2) {
 if (L[i] <= R[j]) {
 arr[k] = L[i];
 i++;
 } else {
 arr[k] = R[j];
 j++;
 }
 k++;
 }
 // Copy remaining elements of L[], if any
 while (i < n1) {
 arr[k] = L[i];
 i++;
 k++;
 }
 // Copy remaining elements of R[], if any
 while (j < n2) {
 arr[k] = R[j];
 j++;
 k++;
 }
 // Free the temporary arrays
 delete[] L;
 delete[] R;
}
// Function to implement merge sort
void mergeSort(int arr[], int left, int right) {
 if (left < right) {
 int mid = left + (right - left) / 2; // To prevent overflow
 // Sort first and second halves
 mergeSort(arr, left, mid);
 mergeSort(arr, mid + 1, right);
 // Merge the sorted halves
 merge(arr, left, mid, right);
 }
}
int main() {
 int arr[] = {5, 45, 49, 11, 7};
 int n = sizeof(arr) / sizeof(arr[0]);
 // Start time
 auto start = high_resolution_clock::now();
 // Perform merge sort
 mergeSort(arr, 0, n - 1);
 // End time
 auto end = high_resolution_clock::now();
 // Calculate the duration of sorting
 auto duration = duration_cast<microseconds>(end - start);
 // Output the sorted array
 cout << "Sorted array: ";
 for (int i = 0; i < n; i++) {
 cout << arr[i] << " ";
 }
 cout << endl;
 // Print the execution time
 cout << "Execution time: " << duration.count() << " microseconds" << endl;
 return 0;
}



Qucik Sort Code:
#include <iostream>
#include <chrono>
using namespace std;
using namespace std::chrono;
// Function to partition the array
int partition(int arr[], int low, int high) {
 int pivot = arr[high]; // Choosing the last element as pivot
 int i = (low - 1); // Index of smaller element
 for (int j = low; j < high; j++) {
 // If current element is smaller than or equal to pivot
 if (arr[j] <= pivot) {
 i++; // Increment index of smaller element
 swap(arr[i], arr[j]); // Swap
 }
 }
 swap(arr[i + 1], arr[high]); // Swap the pivot element with the element at i + 1
 return (i + 1); // Return the partitioning index
}
// Function to implement Quick Sort
void quickSort(int arr[], int low, int high) {
 if (low < high) {
 // Partition the array
 int pi = partition(arr, low, high);
 // Recursively sort elements before and after partition
 quickSort(arr, low, pi - 1);
 quickSort(arr, pi + 1, high);
 }
}
int main() {
 int arr[] = {5, 45, 49, 11, 7}; // Sample array
 int n = sizeof(arr) / sizeof(arr[0]);
 // Start time measurement
 auto start = high_resolution_clock::now();
 // Perform Quick Sort
 quickSort(arr, 0, n - 1);
 // End time measurement
 auto end = high_resolution_clock::now();
 // Calculate the duration of sorting
 auto duration = duration_cast<microseconds>(end - start);
 // Output the sorted array
 cout << "Sorted Array: ";
 for (int i = 0; i < n; i++) {
 cout << arr[i] << " ";
 }
 cout << endl;
 // Print the execution time
 cout << "Execution time: " << duration.count() << " microseconds" << endl;
 return 0;
}



