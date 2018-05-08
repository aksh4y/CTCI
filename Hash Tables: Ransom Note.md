> A kidnapper wrote a ransom note but is worried it will be traced back to him. He found a magazine and wants to know if he can cut out whole words from it and use them to create an untraceable replica of his ransom note. The words in his note are case-sensitive and he must use whole words available in the magazine, meaning he cannot use substrings or concatenation to create the words he needs.

> Given the words in the magazine and the words in the ransom note, print Yes if he can replicate his ransom note exactly using whole words from the magazine; otherwise, print No.

```java
import java.util.*;

public class Solution {
    Map<String, Integer> magazineMap;
    Map<String, Integer> noteMap;
    
    public Solution(String magazine, String note) {
        magazineMap = new HashMap<String, Integer>();
        noteMap = new HashMap<String, Integer>();
        String[] words = magazine.split(" ");
        for (int i = 0; i < words.length;i++) {
            if(magazineMap.containsKey(words[i]))
                magazineMap.put(words[i], magazineMap.get(words[i]) + 1);
            else
                magazineMap.put(words[i], 1);
        }
        words = note.split(" ");
        for (int i = 0; i < words.length;i++) {
            if(noteMap.containsKey(words[i]))
                noteMap.put(words[i], noteMap.get(words[i]) + 1);
            else
                noteMap.put(words[i], 1);
        }
    }
    
    public boolean solve() {
        for(String key : noteMap.keySet()) {
            if(!magazineMap.containsKey(key))
                return false;
            if(magazineMap.get(key) < noteMap.get(key))
                return false;
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int m = scanner.nextInt();
        int n = scanner.nextInt();
        
        // Eat whitespace to beginning of next line
        scanner.nextLine();
        
        Solution s = new Solution(scanner.nextLine(), scanner.nextLine());
        scanner.close();
            
        boolean answer = s.solve();
        if(answer)
            System.out.println("Yes");
        else System.out.println("No");
      
    }
}
```
