> Given an input stream of n integers, you must perform the following task for each ith integer:
Add the ith integer to a running list of integers.
Find the median of the updated list (i.e., for the first element through the ith element).
Print the list's updated median on a new line. The printed value must be a double-precision number scaled to 1 decimal place (i.e., 12.3 format).

```java
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {



    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        int n = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        int[] a = new int[n];
        ArrayList<Integer> lst = new ArrayList<Integer>();
        float res = 0;

        for (int i = 0; i < n; i++) {
            int aItem = scanner.nextInt();
            scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");
            a[i] = aItem;
            int pos = Collections.binarySearch(lst, a[i]);
            if (pos < 0) pos = Math.abs(pos)-1;
                lst.add(pos, a[i]);
            System.out.printf( "%.1f\n", getMedian(lst));
        }

        scanner.close();
    }
    
    public static float getMedian(ArrayList<Integer> lst) {
        if(lst.size() %2 != 0)
            return lst.get(lst.size()/2);
        return (float) (lst.get(lst.size()/2-1) + lst.get(lst.size()/2))/2;
    }
}
```
