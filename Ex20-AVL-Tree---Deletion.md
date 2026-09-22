# Ex20 Sorting an Array using Merge Sort Algorithm
## AIM:
To design a program that sorts a given array of integers in ascending order without using built-in sorting functions, achieving O(n log n) time complexity and minimal space usage.
## Algorithm
1. Start the program.
2. Read the size of the array and input its elements.
3. Use the merge sort function:
   
   Divide the array into two halves recursively until each sub-array has one element.

4. Merge the sorted halves:
 
   Compare the elements of both halves

5. Insert the smallest element into the new array and continue until both halves are merged.

6. Print the sorted array.

7. Stop the program.  

## Program:
```
/*
Program tosorts a given array of integers in ascending order without using built-in sorting functions
Developed by: kirthick roshan j
RegisterNumber: 212223040097
*/
import java.util.*;

public class MergeSort {
    
    // Merge function
    public static void merge(int arr[], int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int L[] = new int[n1];
        int R[] = new int[n2];

        for (int i = 0; i < n1; ++i)
            L[i] = arr[left + i];

        for (int j = 0; j < n2; ++j)
            R[j] = arr[mid + 1 + j];

        int i = 0, j = 0;
        int k = left;

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

        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }

    // Merge Sort function
    public static void mergeSort(int arr[], int left, int right) {
        if (left < right) {
            int mid = (left + right) / 2;

            mergeSort(arr, left, mid);
            mergeSort(arr, mid + 1, right);
            merge(arr, left, mid, right);
        }
    }

    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();

        int arr[] = new int[n];
        System.out.println("Enter elements:");
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        mergeSort(arr, 0, n - 1);

        System.out.println("Sorted Array:");
        for (int x : arr)
            System.out.print(x + " ");
        System.out.println();

        sc.close();
    }
}
```

## Output:


<img width="620" height="297" alt="image" src="https://github.com/user-attachments/assets/a59de798-48be-4bb0-976f-fcb5bac1a2a8" />


## Result:
The program has been successfully implemented and executed.
It sorts the given array of integers in ascending order using the Merge Sort algorithm with a time complexity of O(n log n) and minimal extra space.
