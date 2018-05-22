> In this challenge, you must first implement a queue using two stacks. Then process q queries, where each query is one of the following 3 types:
1. 1 x: Enqueue element x into the end of the queue.
2. 2: Dequeue the element at the front of the queue.
3. 3: Print the element at the front of the queue.

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {
    public static class MyQueue<T> {
        Stack<T> stackNewestOnTop = new Stack<T>();
        Stack<T> stackOldestOnTop = new Stack<T>();

        public void enqueue(T value) { // Push onto newest stack
            stackNewestOnTop.push(value);
        }

        public T peek() {
            if(stackOldestOnTop.isEmpty())
                transferStack();
            T val = stackOldestOnTop.peek();
            return val;
        }

        public T dequeue() {
            if(stackOldestOnTop.isEmpty())
                transferStack();
            T val = stackOldestOnTop.pop();
            return val;
        }
        
        public void transferStack() {
            while(!stackNewestOnTop.isEmpty())
                stackOldestOnTop.push(stackNewestOnTop.pop());
        }
    }

    
    public static void main(String[] args) {
        MyQueue<Integer> queue = new MyQueue<Integer>();
        
        Scanner scan = new Scanner(System.in);
        int n = scan.nextInt();
        
        for (int i = 0; i < n; i++) {
            int operation = scan.nextInt();
            if (operation == 1) { // enqueue
                queue.enqueue(scan.nextInt());
            } else if (operation == 2) { // dequeue
                queue.dequeue();
            } else if (operation == 3) { // print/peek
                System.out.println(queue.peek());
            }
        }
        scan.close();
    }
}
```
