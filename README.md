Repeating element of an array in Java
In this section, we will learn the Program to Find Repeating element of an array in java.Given an array, print all element whose frequency is not equal to one. We will discuss different approaches to print the repeated elements of given input array.

Repeating elements in an array in java
Methods Discussed are :
Method 1 : Using Two loops
Method 2 : Using hash Map.
Method 3 : Using Sorting
Now, let’s discuss the algorithm for both methods.

Method 1 :
In this method we will count the frequency of each elements using two for loops.

To check the status of visited elements create a array of size n.
Run a loop from index 0 to n and check if (visited[i]==1) then skip that element.
Otherwise create a variable count = 1 to keep the count of frequency.
Run a loop from index i+1 to n
Check if(arr[i]==arr[j]), then increment the count by 1 and set visited[j]=1.
After complete iteration of inner for loop and print the element if(count!=1)
Time and Space Complexity :
Time Complexity : O(n2)
Space Complexity : O(n)
Method 1 : Code in Java
Run
import java.util.Arrays;

class Main
{
   public static void countFreq(int arr[], int n)
   {
         boolean visited[] = new boolean[n];
         Arrays.fill(visited, false);
     
         // Traverse through array elements and
         // count frequencies
         for (int i = 0; i < n; i++) {

            // Skip this element if already processed
            if (visited[i] == true)
             continue;

            // Count frequency
            int count = 1;
            for (int j = i + 1; j < n; j++) {
                if (arr[i] == arr[j]) {
                   visited[j] = true;
                   count++;
                }
            }
            if(count!=1)   
               System.out.println(arr[i]);
   }
} // Driver code 

public static void main(String []args) 
{ 
int arr[] = new int[]{10, 30, 30, 20, 10, 20, 50, 10};
 int n = arr.length; 
countFreq(arr, n); 
} 
}
Related Pages
Finding the Longest Palindrome in an Array

Counting Distinct Elements in an Array

Finding Non Repeating elements in an Array

Removing Duplicate elements from an array

Finding Minimum scalar product of two vectors

Output
10
30
20
Method 2 :
In this method we will count use hash-map to count the frequency of each elements.

Declare a hash map
Start iterating over the entire array
If element is present in map, then increase the value of frequency by 1.
Otherwise, insert that element in map.
After complete iteration over array, start traversing map and if(value==1) then print that element.
Time and Space Complexity :
Time Complexity : O(n)
Space Complexity : O(n)
Repeated element in Java
Method 2 : Code in Java
Run
import java.util.*;
import java.util.Arrays;

class Main
{
static void countFreq(int arr[], int n)
{
Map<Integer, Integer> mp = new HashMap<>();

// Traverse through array elements and
// count frequencies
for (int i = 0; i < n; i++)
{
if (mp.containsKey(arr[i]))
{
mp.put(arr[i], mp.get(arr[i]) + 1);
}
else
{
mp.put(arr[i], 1);
}
}
// Traverse through map and print frequencies
for (Map.Entry<Integer, Integer> entry : mp.entrySet())
{ if(entry.getValue()>1)
System.out.println(entry.getKey()+" ");
}

}
// Driver code
public static void main(String []args)
{
int arr[] = new int[]{10, 30, 50, 20, 10, 20, 30, 10};
int n = arr.length;
countFreq(arr, n);
}
}
Output
20 
10 
30 
Method 3 :
In this method it is necessary that the array is sorted. So we will use bubble sort to sort the given array. 

Method 3 : code in Java
Run
import java.util.*;
import java.util.Arrays;

class Main
{
   static int bubbleSort(int arr[], int size){
        for (int i = 0; i < size-1; i++){
            // Since, after each iteration righmost i elements are sorted 
              for (int j = 0; j < size-i-1; j++) if (arr[j] > arr[j+1]) 
              {
                    int temp = arr[j]; // swap the element
                    arr[j] = arr[j+1]; 
                    arr[j+1] = temp; 
              }
         } 
        return 0;
   } 

   static void findRepeating(int arr[], int n){
 
        int count = 0;
        for (int i = 0; i < n; i++) {

             int flag = 0;
             while (i < n - 1 && arr[i] == arr[i + 1]){
               flag = 1;
               i++;
             }
             // since i++ happened, we need to print previous element
             if(flag==1)
               System.out.print(arr[i-1] + " ");
        }
        return;
   }

   // Driver code
   public static void main(String []args)
   {
       int arr[] = new int[]{10, 30, 50, 20, 10, 20, 30, 10};
       int n = arr.length;
       bubbleSort(arr, n);
       findRepeating(arr, n);
   }
}
Output
10 20 30
