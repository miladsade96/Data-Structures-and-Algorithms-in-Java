# Big O:

1. **What is Big O Notation?**  
   Big O notation is a mathematical representation used to describe the performance or complexity of an algorithm in
   terms of time or space as the input size grows. It provides an upper bound on the growth rate of an algorithm's
   resource consumption.
2. **Why is Big O Important?**  
   Understanding Big O notation helps developers analyze and compare the efficiency of different algorithms, allowing
   them to choose the most suitable one for their applications, especially when dealing with large datasets.
3. **What is the difference between Big O, Big Omega, and Big Theta?**
    - Big O (O): Describes the upper bound of an algorithm's growth rate. It indicates the worst-case scenario.
    - Big Omega (Ω): Describes the lower bound of an algorithm's growth rate. It indicates the best-case scenario.
    - Big Theta (Θ): Describes a tight bound on an algorithm's growth rate. It indicates that the algorithm grows at the
      same rate in both the best and worst cases.
4. **Explain O(1) Time Complexity.**  
   O(1) time complexity, also known as constant time complexity, means that the execution time of an algorithm remains
   constant regardless of the input size. An example is accessing an element in an array by its index.
   ```java
    int getElement(int[] array, int index) {
         return array[index]; // O(1)
    }
    ```
5. **Explain O(n) Time Complexity.**  
   O(n) time complexity, also known as linear time complexity, means that the execution time of an algorithm grows
   linearly with the input size. An example is iterating through all elements in a list.
   ```java
    void printElements(int[] array) {
         for (int element : array) {
             System.out.println(element); // O(n)
         }
    }
    ```
6. **Explain O(n^2) Time Complexity.**  
   O(n^2) time complexity, also known as quadratic time complexity, means that the execution time of an algorithm
   grows
   quadratically with the input size. An example is a nested loop that compares each element in a list with every
   other
   element.
   ```java
    void printPairs(int[] array) {
         for (int i = 0; i < array.length; i++) {
             for (int j = 0; j < array.length; j++) {
                 System.out.println(array[i] + ", " + array[j]); // O(n^2)
             }
         }
    }
      ```
7. **What is O(log n) Time Complexity?**  
   O(log n) time complexity, also known as logarithmic time complexity, means that the execution time of an algorithm
   grows logarithmically with the input size. An example is binary search, where the search space is halved with each
   step.
   ```java
    int binarySearch(int[] array, int target) {
         int left = 0;
         int right = array.length - 1;
         while (left <= right) {
             int mid = left + (right - left) / 2;
             if (array[mid] == target) {
                 return mid; // O(log n)
             } else if (array[mid] < target) {
                 left = mid + 1;
             } else {
                 right = mid - 1;
             }
         }
         return -1; // Not found
    }
    ```
8. **What is O(n log n) Time Complexity?**  
   O(n log n) is a time complexity that falls between linear O(n) and quadratic O(n²). It's commonly called "
   linearithmic" or "log-linear" time.The complexity O(n log n) means: For each of the n elements, you perform an
   operation that takes log n time Or you divide the problem in half (log n divisions) and process all n elements at
   each level.

```java
public class MergeSortExample {

    public static void mergeSort(int[] arr, int left, int right) {
        if (left < right) {
            // Find the middle point - O(1)
            int mid = left + (right - left) / 2;

            // Recursively sort first half - log n divisions
            mergeSort(arr, left, mid);

            // Recursively sort second half - log n divisions
            mergeSort(arr, mid + 1, right);

            // Merge the sorted halves - O(n) work per level
            merge(arr, left, mid, right);
        }
    }

    public static void merge(int[] arr, int left, int mid, int right) {
        // Calculate sizes
        int n1 = mid - left + 1;
        int n2 = right - mid;

        // Create temp arrays
        int[] L = new int[n1];
        int[] R = new int[n2];

        // Copy data to temp arrays
        for (int i = 0; i < n1; i++)
            L[i] = arr[left + i];
        for (int j = 0; j < n2; j++)
            R[j] = arr[mid + 1 + j];

        // Merge the temp arrays back
        int i = 0, j = 0, k = left;

        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k++] = L[i++];
            } else {
                arr[k++] = R[j++];
            }
        }

        // Copy remaining elements
        while (i < n1) arr[k++] = L[i++];
        while (j < n2) arr[k++] = R[j++];
    }

    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};

        System.out.println("Original array:");
        printArray(arr);

        mergeSort(arr, 0, arr.length - 1);

        System.out.println("\nSorted array:");
        printArray(arr);
    }

    public static void printArray(int[] arr) {
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();
    }

}

```

9. **Explain dropping constants and non-dominant terms in Big O notation.**  
   In Big O notation, we focus on the dominant term that has the most significant impact on the growth rate of an
   algorithm as the input size increases. Constants and non-dominant terms are dropped because they become negligible
   for large input sizes. For example, O(2n + 3) simplifies to O(n) because the linear term n dominates the constant
   factors as n grows larger.

10. **Explain different terms of input size in Big O notation(in case we have n and m as inputs).**
    - When analyzing algorithms with multiple input sizes, we can express the time complexity in terms of both inputs.
      For example, if an algorithm processes two separate lists of sizes n and m, the time complexity might be expressed
      as O(n + m) if it processes each list independently.
    - In cases where one input size dominates the other, we can simplify the notation. For instance, if n is much larger
      than m, O(n + m) can be approximated as O(n).
    - If the algorithm's complexity depends on the product of the two input sizes, it can be expressed as O(n * m).
      This is common in algorithms that involve nested loops iterating over both inputs.
    - When analyzing algorithms with multiple inputs, it's essential to consider how each input size affects the overall
      complexity and express it accordingly in Big O notation.

11. **What is space complexity?**  
    Space complexity refers to the amount of memory an algorithm uses in relation to the size of the input data. It
    considers both the fixed part of the memory (e.g., variables, constants) and the variable part (e.g., dynamic data
    structures) that grows with the input size. Space complexity is often expressed using Big O notation, similar to
    time
    complexity. For example, an algorithm that uses an array of size n would have a space complexity of O(n).
