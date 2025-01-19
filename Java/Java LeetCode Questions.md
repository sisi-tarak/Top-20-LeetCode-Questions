# Top 20 Java LeetCode Interview Questions & Solutions 🚀

Welcome to the **Top 20 Java LeetCode Interview Questions** repository! Whether you're prepping for coding interviews or looking to improve your problem-solving skills, this repository is a curated collection of the most essential LeetCode problems that you’ll encounter in interviews. Each problem is followed by a clear and efficient solution in Java, along with an explanation to ensure you understand the concepts behind it.

### 🌟 Why This Repo?

- **Top 20 must-know LeetCode problems** every coder should master for technical interviews.
- **Detailed explanations** and **step-by-step solutions** for each problem.
- Optimized solutions to help you improve **time complexity** and **space efficiency**.
- Perfect for **interview prep** and **competitive programming**.

### 🚀 What You’ll Find:

- **Problem 1 - Problem 20:** Each problem is chosen based on its relevance in real-world interviews and coding challenges.
- **Clean and efficient Java solutions** with comments for easy understanding.
- **Explanations** to help you understand the thought process behind the solution.
- Solutions covering a range of topics: arrays, dynamic programming, trees, graphs, and more.

### 🔑 Why Star This Repo?

- Stay **updated** as we continue to add more problems and optimize existing solutions.
- Get access to a **ready-to-go** interview preparation guide.
- A simple way to contribute back to the community by **star**-ing this repo!

If you're looking to **ace your coding interviews** or simply want to practice the **most common questions** asked in interviews, this repository will be your go-to guide.

Don’t forget to hit the **star** ⭐ to keep this repository in your favorites and help others discover it!

### 📈 Start Practicing Now!

Dive into the questions, sharpen your skills, and keep coming back for more interview prep!

Happy Coding and Good Luck with your Interviews! 💻✨

---

## 1. Two Sum

- **Problem:** Given an array of integers `nums` and an integer `target`, return _indices_ of the two numbers such that they add up to `target`.

- **Java Code:**

```java
import java.util.HashMap;
import java.util.Map;

public class TwoSum {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        return new int[] {};
    }
}
```

- **Explanation:**
  - We use a `HashMap` to store each number and its index.
  - For each number `num` in the array:
    - Calculate the `complement` needed to reach the `target`.
    - If the `complement` exists in the `HashMap`, we have found the pair. Return the indices.
    - Otherwise, add the current `num` and its index to the `HashMap`.

## 2. Reverse Linked List

- **Problem:** Reverse a singly linked list.

- **Java Code:**

```java
class ListNode {
    int val;
    ListNode next;
    ListNode() {}
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
}

public class ReverseLinkedList {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        while (curr != null) {
            ListNode nextTemp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextTemp;
        }
        return prev;
    }
}
```

- **Explanation:**
  - Initialize `prev` to `null` and `curr` to the `head` of the list.
  - Iterate through the list:
    - Store the `next` node of the current node in `nextTemp`.
    - Reverse the link of the current node: `curr.next = prev`.
    - Move `prev` to the current node: `prev = curr`.
    - Move `curr` to the `nextTemp`.
  - After the loop, `prev` will point to the head of the reversed list.

## 3. Valid Parentheses

- **Problem:** Determine if a string containing only parentheses `()`, `{}`, `[]` is valid.

- **Java Code:**

```java
import java.util.Stack;

public class ValidParentheses {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            if (c == '(') stack.push(')');
            else if (c == '{') stack.push('}');
            else if (c == '[') stack.push(']');
            else if (stack.isEmpty() || stack.pop() != c) return false;
        }
        return stack.isEmpty();
    }
}
```

- **Explanation:**
  - Use a stack to keep track of opening parentheses.
  - Iterate through the string:
    - If the character is an opening parenthesis, push the corresponding closing parenthesis onto the stack.
    - If the character is a closing parenthesis:
      - If the stack is empty or the top of the stack doesn't match the current character, the string is invalid.
  - After iterating, the stack should be empty if all parentheses are valid.

## 4. Merge Two Sorted Lists

- **Problem:** Merge two sorted linked lists into one sorted list.

- **Java Code:**

```java
public class MergeTwoSortedLists {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode();
        ListNode tail = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                tail.next = list1;
                list1 = list1.next;
            } else {
                tail.next = list2;
                list2 = list2.next;
            }
            tail = tail.next;
        }

        tail.next = (list1 != null) ? list1 : list2;
        return dummy.next;
    }
}
```

- **Explanation:**
  - Create a dummy node to simplify the logic.
  - Initialize a `tail` pointer to the dummy node.
  - Iterate through both lists:
    - Compare the values of the current nodes in `list1` and `list2`.
    - Append the node with the smaller value to the `tail` and move the corresponding pointer forward.
  - If one list becomes empty, append the remaining nodes of the other list to the `tail`.
  - Return the head of the merged list (the next node of the dummy node).

## 5. Longest Substring Without Repeating Characters

- **Problem:** Find the length of the longest substring without repeating characters.

- **Java Code:**

```java
import java.util.HashSet;
import java.util.Set;

public class LongestSubstringWithoutRepeatingCharacters {
    public int lengthOfLongestSubstring(String s) {
        Set<Character> set = new HashSet<>();
        int left = 0;
        int maxLen = 0;

        for (int right = 0; right < s.length(); right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLen = Math.max(maxLen, right - left + 1);
        }

        return maxLen;
    }
}
```

- **Explanation:**
  - Use a sliding window approach.
  - Maintain a `HashSet` to store characters in the current window.
  - Iterate through the string:
    - If the current character is already in the `HashSet`, remove characters from the beginning of the window until the duplicate character is removed.
    - Add the current character to the `HashSet`.
    - Update the `maxLen` if the current window size is greater.



## 6. Climbing Stairs

- **Problem:** You are climbing a staircase. It takes `n` steps to reach the top. Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

- **Java Code:**

```java
public class ClimbingStairs {
    public int climbStairs(int n) {
        if (n <= 1) {
            return 1;
        }
        int[] dp = new int[n + 1];
        dp[0] = 1;
        dp[1] = 1;
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }
}
```

- **Explanation:**
  - This problem can be solved using dynamic programming.
  - Create a `dp` array to store the number of ways to reach each step.
  - Initialize `dp[0]` and `dp[1]` to 1 (base cases).
  - Iterate from step 2 to `n`:
    - The number of ways to reach step `i` is the sum of ways to reach step `i-1` and step `i-2`.
  - Return the number of ways to reach step `n` (stored in `dp[n]`).

## 7. Binary Search

- **Problem:** Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write an efficient algorithm that searches for `target` in `nums`. If `target` is found, return its index. Otherwise, return `-1`.

- **Java Code:**

```java
public class BinarySearch {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return -1;
    }
}
```

- **Explanation:**
  - Initialize `left` and `right` pointers to the beginning and end of the array, respectively.
  - While `left` is less than or equal to `right`:
    - Calculate the `mid` index.
    - If `nums[mid]` is equal to the `target`, return the `mid` index.
    - If `nums[mid]` is less than the `target`, update `left` to `mid + 1`.
    - If `nums[mid]` is greater than the `target`, update `right` to `mid - 1`.
  - If the loop completes without finding the `target`, return `-1`.

## 8. Implement Queue using Stacks

- **Problem:** Implement a first-in, first-out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a standard queue (`push`, `pop`, `peek`, `empty`).

- **Java Code:**

```java
import java.util.Stack;

class MyQueue {
    private Stack<Integer> stack1;
    private Stack<Integer> stack2;

    public MyQueue() {
        stack1 = new Stack<>();
        stack2 = new Stack<>();
    }

    public void push(int x) {
        stack1.push(x);
    }

    public int pop() {
        if (stack2.isEmpty()) {
            while (!stack1.isEmpty()) {
                stack2.push(stack1.pop());
            }
        }
        return stack2.pop();
    }

    public int peek() {
        if (stack2.isEmpty()) {
            while (!stack1.isEmpty()) {
                stack2.push(stack1.pop());
            }
        }
        return stack2.peek();
    }

    public boolean empty() {
        return stack1.isEmpty() && stack2.isEmpty();
    }
}
```

- **Explanation:**
  - We use two stacks:
    - `stack1`: Primarily used for `push` operations.
    - `stack2`: Primarily used for `pop` and `peek` operations.
  - `push(x)`: Simply push `x` onto `stack1`.
  - `pop()`:
    - If `stack2` is empty, transfer all elements from `stack1` to `stack2` (reversing the order).
    - Pop and return the top element from `stack2`.
  - `peek()`:
    - If `stack2` is empty, transfer all elements from `stack1` to `stack2`.
    - Return the top element of `stack2`.
  - `empty()`: Return `true` if both `stack1` and `stack2` are empty.

## 9. Valid Palindrome

- **Problem:** Determine whether a given string is a palindrome.

- **Java Code:**

```java
public class ValidPalindrome {
    public boolean isPalindrome(String s) {
        int left = 0;
        int right = s.length() - 1;

        while (left < right) {
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            }
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            }
            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            }
            left++;
            right--;
        }

        return true;
    }
}
```

- **Explanation:**
  - Initialize `left` and `right` pointers to the beginning and end of the string, respectively.
  - While `left` is less than `right`:
    - Move `left` to the next alphanumeric character.
    - Move `right` to the previous alphanumeric character.
    - Compare the characters at `left` and `right` (ignoring case). If they are not equal, return `false`.
  - If the loop completes without finding any mismatches, return `true`.


## 10. Merge Sorted Array

- **Problem:** Given two sorted integer arrays `nums1` and `nums2`, merge `nums2` into `nums1` in such a way that it becomes a single, sorted array.

- **Java Code:**

```java
public class MergeSortedArray {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int p1 = m - 1; // Pointer for nums1
        int p2 = n - 1; // Pointer for nums2
        int p = m + n - 1; // Pointer for the merged array

        while (p2 >= 0) {
            if (p1 >= 0 && nums1[p1] > nums2[p2]) {
                nums1[p] = nums1[p1];
                p1--;
            } else {
                nums1[p] = nums2[p2];
                p2--;
            }
            p--;
        }
    }
}
```

- **Explanation:**
  - Initialize pointers `p1`, `p2`, and `p` as described above.
  - Compare `nums1[p1]` and `nums2[p2]`:
    - If `nums1[p1]` is greater than `nums2[p2]`, place `nums1[p1]` at `nums1[p]`.
    - Otherwise, place `nums2[p2]` at `nums1[p]`.
  - Decrement the appropriate pointers (`p1` or `p2`) and the main pointer `p`.
  - Continue until `p2` reaches 0.

## 11. Remove Duplicates from Sorted Array

- **Problem:** Given an integer array `nums` sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

- **Java Code:**

```java
public class RemoveDuplicatesFromSortedArray {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) {
            return 0;
        }

        int slow = 0;
        for (int fast = 1; fast < nums.length; fast++) {
            if (nums[slow] != nums[fast]) {
                slow++;
                nums[slow] = nums[fast];
            }
        }

        return slow + 1;
    }
}
```

- **Explanation:**
  - Initialize `slow` and `fast` pointers.
  - Iterate through the array:
    - If `nums[slow]` is different from `nums[fast]`, increment `slow` and place `nums[fast]` at `nums[slow]`.
  - Return `slow + 1` as the length of the array after removing duplicates.

## 12. String to Integer (a to i)

- **Problem:** Implement the `myAtoi(string s)` function, which converts a string to an integer.

- **Java Code:**

```java
public class StringToInteger {
    public int myAtoi(String s) {
        s = s.trim();
        if (s.isEmpty()) {
            return 0;
        }

        boolean isNegative = false;
        if (s.charAt(0) == '-') {
            isNegative = true;
            s = s.substring(1);
        } else if (s.charAt(0) == '+') {
            s = s.substring(1);
        }

        long result = 0;
        for (char c : s.toCharArray()) {
            if (!Character.isDigit(c)) {
                break;
            }
            result = result * 10 + (c - '0');
            if (result > Integer.MAX_VALUE) {
                return isNegative ? Integer.MIN_VALUE : Integer.MAX_VALUE;
            }
        }

        return isNegative ? (int) -result : (int) result;
    }
}
```

- **Explanation:**
  - Remove leading and trailing whitespaces.
  - Handle the sign (positive or negative).
  - Iterate through the characters:
    - If the character is not a digit, break the loop.
    - Convert the digit to an integer and add it to the `result`.
    - Check for integer overflow/underflow.
  - Return the `result` multiplied by the `sign`.

## 13. Longest Common Prefix

- **Problem:** Write a function to find the longest common prefix string amongst an array of strings.

- **Java Code:**

```java
public class LongestCommonPrefix {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) {
            return "";
        }

        String prefix = strs[0];
        for (int i = 1; i < strs.length; i++) {
            while (!strs[i].startsWith(prefix)) {
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

- **Explanation:**
  - Initialize `prefix` to the first string in the array.
  - Iterate through the remaining strings:
    - While the current string does not start with the `prefix`, shorten the `prefix` by one character.
    - If the `prefix` becomes empty, return an empty string.
  - Return the final `prefix`.

## 14. Roman to Integer

- **Problem:** Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D`, and `M`. Given a roman numeral, convert it to an integer.

- **Java Code:**

```java
import java.util.HashMap;
import java.util.Map;

public class RomanToInteger {
    public int romanToInt(String s) {
        Map<Character, Integer> romanMap = new HashMap<>();
        romanMap.put('I', 1);
        romanMap.put('V', 5);
        romanMap.put('X', 10);
        romanMap.put('L', 50);
        romanMap.put('C', 100);
        romanMap.put('D', 500);
        romanMap.put('M', 1000);

        int result = 0;
        int prevVal = 0;

        for (int i = s.length() - 1; i >= 0; i--) {
            int currVal = romanMap.get(s.charAt(i));
            if (currVal < prevVal) {
                result -= currVal;
            } else {
                result += currVal;
            }
            prevVal = currVal;
        }

        return result;
    }
}
```

- **Explanation:**
  - Create a `HashMap` to store the integer values of Roman numerals.
  - Iterate through the Roman numeral string in reverse order:
    - If the current value is less than the previous value, subtract the current value from the `result`.
    - Otherwise, add the current value to the `result`.

## 15. Container With Most Water

- **Problem:** Given an integer array `height` of length `n`, where `height[i]` is the height of the `i`-th line on the x-axis, find two lines that together with the x-axis form a container, such that the container contains the most water.

- **Java Code:**

```java
public class ContainerWithMostWater {
    public int maxArea(int[] height) {
        int left = 0;
        int right = height.length - 1;
        int maxArea = 0;

        while (left < right) {
            int area = Math.min(height[left], height[right]) * (right - left);
            maxArea = Math.max(maxArea, area);

            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }

        return maxArea;
    }
}
```

- **Explanation:**
  - Initialize `left` and `right` pointers to the beginning and end of the array.
  - Calculate the area of the container formed by the current `left` and `right` pointers.
  - Update `maxArea` if the current area is greater.
  - Move the pointer with the shorter height inward (to potentially increase the area).
  - Repeat until `left` and `right` pointers meet.

## 16. 3Sum

- **Problem:** Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

- **Java Code:**

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class ThreeSum {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();

        for (int i = 0; i < nums.length - 2; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            int left = i + 1;
            int right = nums.length - 1;

            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (sum == 0) {
                    result.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    while (left < right && nums[left] == nums[left + 1]) {
                        left++;
                    }
                    while (left < right && nums[right] == nums[right - 1]) {
                        right--;
                    }
                    left++;
                    right--;
                } else if (sum < 0) {
                    left++;
                } else {
                    right--;
                }
            }
        }

        return result;
    }
}
```

- **Explanation:**
  - Sort the `nums` array.
  - Iterate through the array using the `i` pointer:
    - Skip duplicate values for `nums[i]`.
    - Initialize `left` and `right` pointers.
    - While `left` is less than `right`:
      - Calculate the sum of `nums[i]`, `nums[left]`, and `nums[right]`.
      - If the sum is 0, add the triplet to the `result` and skip duplicate values for `nums[left]` and `nums[right]`.
      - If the sum is less than 0, move the `left` pointer to the right.
      - If the sum is greater than 0, move the `right` pointer to the left.
  - Return the list of triplets.

## 17. Letter Combinations of a Phone Number

- **Problem:** Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

- **Java Code:**

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class LetterCombinationsOfPhoneNumber {
    public List<String> letterCombinations(String digits) {
        if (digits.isEmpty()) {
            return new ArrayList<>();
        }

        Map<Character, String> digitToLetters = new HashMap<>();
        digitToLetters.put('2', "abc");
        digitToLetters.put('3', "def");
        digitToLetters.put('4', "ghi");
        digitToLetters.put('5', "jkl");
        digitToLetters.put('6', "mno");
        digitToLetters.put('7', "pqrs");
        digitToLetters.put('8', "tuv");
        digitToLetters.put('9', "wxyz");

        List<String> result = new ArrayList<>();
        backtrack(digits, 0, new StringBuilder(), digitToLetters, result);
        return result;
    }

    private void backtrack(String digits, int index, StringBuilder currentString, Map<Character, String> digitToLetters, List<String> result) {
        if (index == digits.length()) {
            result.add(currentString.toString());
            return;
        }

        String letters = digitToLetters.get(digits.charAt(index));
        for (char letter : letters.toCharArray()) {
            currentString.append(letter);
            backtrack(digits, index + 1, currentString, digitToLetters, result);
            currentString.deleteCharAt(currentString.length() - 1);
        }
    }
}
```

- **Explanation:**
  - Create a `HashMap` to map digits to their corresponding letters.
  - Use backtracking to explore all possible combinations.
    - The `backtrack` function recursively explores each digit and adds its corresponding letters to the `currentString`.
    - When the `index` reaches the end of the `digits` string, add the `currentString` to the `result` list.

## 18. Combination Sum

- **Problem:** Given an array of distinct integers `candidates` and a target integer `target`, return a list of all unique combinations of `candidates` where the numbers in each combination add up to `target`. You may return the combinations in any order.

- **Java Code:**

```java
import java.util.ArrayList;
import java.util.List;

public class CombinationSum {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(candidates, target, 0, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] candidates, int target, int start, List<Integer> current, List<List<Integer>> result) {
        if (target == 0) {
            result.add(new ArrayList<>(current));
            return;
        }

        if (target < 0) {
            return;
        }

        for (int i = start; i < candidates.length; i++) {
            current.add(candidates[i]);
            backtrack(candidates, target - candidates[i], i, current, result);
            current.remove(current.size() - 1);
        }
    }
}
```

- **Explanation:**
  - Use backtracking to explore all possible combinations.
    - The `backtrack` function recursively explores each candidate:
      - If the `target` reaches 0, add the `current` combination to the `result`.
      - If the `target` becomes negative, stop the recursion.
      - Include the current `candidate` in the `current` combination and recursively explore further.
      - Backtrack by removing the current `candidate` from the `current` combination.
      - Explore the next `candidate` without including the current one.

## 19. Permutations

- **Problem:** Given an array `nums` of distinct integers, return all the possible permutations. You can return the answer in any order.

- **Java Code:**

```java
import java.util.ArrayList;
import java.util.List;

public class Permutations {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        backtrack(nums, new ArrayList<>(), result);
        return result;
    }

    private void backtrack(int[] nums, List<Integer> current, List<List<Integer>> result) {
        if (current.size() == nums.length) {
            result.add(new ArrayList<>(current));
            return;
        }

        for (int num : nums) {
            if (!current.contains(num)) {
                current.add(num);
                backtrack(nums, current, result);
                current.remove(current.size() - 1);
            }
        }
    }
}
```

- **Explanation:**
  - Use backtracking to explore all possible permutations.
    - The `backtrack` function recursively explores each number in the `nums` array:
      - If the `current` permutation has the same length as `nums`, add it to the `result`.
      - If the `num` is not already in the `current` permutation, add it to the `current` permutation and recursively explore further.
      - Backtrack by removing the `num` from the `current` permutation.

## 20. Subsets

- **Problem:** Given an integer array `nums`, return all possible subsets (the power set). The solution must not contain duplicate subsets.

- **Java Code:**

```java
import java.util.ArrayList;
import java.util.List;

public class Subsets {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        result.add(new ArrayList<>());

        for (int num : nums) {
            int n = result.size();
            for (int i = 0; i < n; i++) {
                List<Integer> newSubset = new ArrayList<>(result.get(i));
                newSubset.add(num);
                result.add(newSubset);
            }
        }

        return result;
    }
}
```

- **Explanation:**
  - Start with an empty set (an empty list) in the `result`.
  - Iterate through each number in `nums`:
    - Create new subsets by adding the current `num` to each existing subset in the `result`.
    - Add the new subsets to the `result`.

<br/><br/>

## Usage 🚀

Each code snippet includes a sample usage example. To run the code:

1. Copy the Java code into your development environment (e.g., VSCode, IntelliJ, or Jupyter Notebook).
2. Replace sample inputs with your custom test cases as needed.
3. Execute the code and verify the results.

## Contribution 💻

If you'd like to contribute to this repository:

1. Fork the repository.
2. Create a new branch: `git checkout -b feature/new-feature`.
3. Make your changes and commit them: `git commit -m "Add new feature"`.
4. Push to the branch: `git push origin feature/new-feature`.
5. Submit a pull request.

<br/>

Don’t forget to hit the **star** ⭐ to keep this repository in your favorites and help others discover it!

---

Feel free to ask for more algorithm explanations or additional features! 😊
