# Longest Common Prefix (LCP)

## Description

This project contains a Java solution to find the **Longest Common Prefix** among a given array of strings. The longest common prefix is the longest substring that appears at the beginning of all strings in the array.

## Problem Statement

Given an array of strings `strs`, return the longest common prefix string amongst all strings present in the array. If there is no common prefix, return an empty string `""`.

### Examples

**Example 1:**
```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```

**Example 2:**
```
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Example 3:**
```
Input: strs = ["a"]
Output: "a"
```

## Solution Approach

The solution uses a **horizontal scanning approach**:

1. Start with the first string as the initial prefix
2. For each subsequent string, check if it starts with the current prefix
3. If it doesn't, trim the prefix from the end until a match is found
4. If the prefix becomes empty, return an empty string
5. Return the final prefix after checking all strings

### Algorithm Complexity

- **Time Complexity:** O(n × m²), where n is the number of strings and m is the minimum length of any string (due to substring operations)
- **Space Complexity:** O(1), only using constant extra space

## Code

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
       
        if (strs == null || strs.length == 0) {
            return "";
        }
        
       
        String prefix = strs[0];
        
       
        for (int i = 1; i < strs.length; i++) {
            
          
            while (strs[i].indexOf(prefix) != 0) {
              
                prefix = prefix.substring(0, prefix.length() - 1);
             
                if (prefix.isEmpty()) {
                    return "";
                }
            }
        }
        
       
        return prefix;
    }
}
```

## How to Use

### Compile
```bash
javac lcp.java
```

### Create a Test Class
```java
public class Main {
    public static void main(String[] args) {
        Solution solution = new Solution();
        
        String[] strs1 = {"flower", "flow", "flight"};
        System.out.println(solution.longestCommonPrefix(strs1)); // Output: "fl"
        
        String[] strs2 = {"dog", "racecar", "car"};
        System.out.println(solution.longestCommonPrefix(strs2)); // Output: ""
        
        String[] strs3 = {"a"};
        System.out.println(solution.longestCommonPrefix(strs3)); // Output: "a"
    }
}
```

### Run
```bash
java Main
```

## Edge Cases Handled

- Empty array → returns ""
- Single string → returns the entire string
- No common prefix → returns ""
- Null input → returns ""
- Single character strings → returns "" or that character

## Alternative Approaches

1. **Vertical Scanning:** Compare characters column by column (O(n × m) time)
2. **Divide & Conquer:** Split array in half and find LCP recursively
3. **Trie-based:** Build a trie and traverse the path of common characters
4. **Binary Search:** Binary search on prefix length

## License

This code is open source and available for educational purposes.

## Author

Created as part of DSA (Data Structures and Algorithms) practice.
