> A left rotation operation on an array of size n shifts each of the array's elements 1 unit to the left. 
For example, if 2 left rotations are performed on array [1, 2, 3, 4, 5], then the array would become [3, 4, 5, 1, 2]. 
Given an array of n integers and a number, d, perform d left rotations on the array. 
Then print the updated array as a single line of space-separated integers.


```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {

    public static int[] arrayLeftRotation(int[] a, int n, int k) {
        if(k == 0 || n <= 1)
            return a;
        
        int temp = a[0];
        for(int i = 0; i < n - 1; i++) {
            a[i] = a[i+1];
        }
        a[n-1] = temp;
        return arrayLeftRotation(a, n, --k);        
    }
    
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int n = in.nextInt();
        int k = in.nextInt();
        int a[] = new int[n];
        for(int a_i=0; a_i < n; a_i++){
            a[a_i] = in.nextInt();
        }
      
        int[] output = new int[n];
        output = arrayLeftRotation(a, n, k);
        for(int i = 0; i < n; i++)
            System.out.print(output[i] + " ");
      
        System.out.println();
      
    }
}
```
