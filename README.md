# Valid Anagram
# https://leetcode.com/problems/valid-anagram

Given two strings s and t , write a function to determine if t is an anagram of s.
```
Example 1:

Input: s = "anagram", t = "nagaram"
Output: true
Example 2:

Input: s = "rat", t = "car"
Output: false
```
**Note:**
You may assume the string contains only lowercase alphabets.

**Follow up:**
What if the inputs contain unicode characters? How would you adapt your solution to such case?


# Implementation 1 : Sorting

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) 
            return false;
        
        char[] str1 = s.toCharArray();
        char[] str2 = t.toCharArray();
        Arrays.sort(str1);
        Arrays.sort(str2);
        return Arrays.equals(str1, str2);
    }
}
```

# Implementation 2 : Hashing
```java
class Solution {
    public boolean isAnagram(String s, String t) {
       if (s.length() != t.length()) 
         return false;
      
       int[] chars = new int[26];
       for (int i = 0; i < s.length(); i++) 
            chars[s.charAt(i) - 'a']++;
      
       for (int i = 0; i < t.length(); i++) {
            chars[t.charAt(i) - 'a']--;
            if (chars[t.charAt(i) - 'a'] < 0) {
                return false;
            }
       }
      return true;
   }
}
```

# Follow up :
What if the inputs contain unicode characters? How would you adapt your solution to such case?
**Answer :**
Use a hash table instead of a fixed size counter. Imagine allocating a large size array to fit the entire range of unicode characters, which could go up to more than 1 million. A hash table is a more generic solution and could adapt to any range of characters.

# References :
https://leetcode.com/articles/valid-anagram
