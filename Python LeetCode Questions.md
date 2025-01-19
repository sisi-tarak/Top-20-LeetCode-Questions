


**1. Two Sum**

* **Problem:** Given an array of integers `nums` and an integer `target`, return *indices* of the two numbers such that they add up to `target`.

* **Python Code:**

```python
def two_sum(nums, target):
    """
    Finds the indices of two numbers in the list that add up to the target.

    Args:
        nums: A list of integers.
        target: The target sum.

    Returns:
        A list containing the indices of the two numbers.
        Returns an empty list if no such pair exists.
    """
    seen = {}  # Dictionary to store seen numbers and their indices
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i
    return []  # No solution found

# Example usage
nums = [2, 7, 11, 15]
target = 9
result = two_sum(nums, target)
print(result)  # Output: [0, 1]
```

* **Explanation:**
    * We use a dictionary (`seen`) to store the numbers we have encountered and their corresponding indices.
    * For each number `num` in the list:
        * Calculate the `complement` needed to reach the `target`.
        * If the `complement` is already in the `seen` dictionary, we have found the pair. Return the indices.
        * Otherwise, add the current `num` and its index to the `seen` dictionary.
    * If no pair is found, return an empty list.

**2. Reverse Linked List**

* **Problem:** Reverse a singly linked list.

* **Python Code:**

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverse_list(head):
    """
    Reverses a singly linked list.

    Args:
        head: The head of the linked list.

    Returns:
        The head of the reversed linked list.
    """
    prev = None
    curr = head
    while curr:
        next_node = curr.next
        curr.next = prev
        prev = curr
        curr = next_node
    return prev

# Example usage (assuming you have a function to create a linked list)
head = create_linked_list([1, 2, 3, 4, 5])  # Create a linked list
reversed_head = reverse_list(head)
# Print the reversed linked list (implementation of printing depends on your ListNode class)
```

* **Explanation:**
    * Initialize `prev` to `None` (previous node) and `curr` to the `head` of the list.
    * Iterate through the list:
        * Store the `next` node of the current node in `next_node`.
        * Reverse the link of the current node: `curr.next = prev`.
        * Move `prev` to the current node: `prev = curr`.
        * Move `curr` to the `next_node`.
    * After the loop, `prev` will point to the head of the reversed list.

**3. Valid Parentheses**

* **Problem:** Determine if a string containing only parentheses `()`, `{}`, `[]` is valid.

* **Python Code:**

```python
def is_valid(s):
    """
    Checks if a string of parentheses is valid.

    Args:
        s: The string of parentheses.

    Returns:
        True if the string is valid, False otherwise.
    """
    stack = []
    mapping = {')': '(', '}': '{', ']': '['}
    for char in s:
        if char in mapping:  # Closing parenthesis
            if not stack or stack.pop() != mapping[char]:
                return False
        else:  # Opening parenthesis
            stack.append(char)
    return not stack  # Stack should be empty if all parentheses are valid

# Example usage
s1 = "()"
s2 = "()[]{}"
s3 = "(]"
print(is_valid(s1))  # Output: True
print(is_valid(s2))  # Output: True
print(is_valid(s3))  # Output: False
```

* **Explanation:**
    * Use a stack to keep track of opening parentheses.
    * Iterate through the string:
        * If the character is a closing parenthesis:
            * If the stack is empty or the top of the stack doesn't match the corresponding opening parenthesis, the string is invalid.
        * If the character is an opening parenthesis, push it onto the stack.
    * After iterating, the stack should be empty if all parentheses are valid.


**4. Merge Two Sorted Lists**

* **Problem:** Merge two sorted linked lists into one sorted list.

* **Python Code:**

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def merge_two_lists(list1, list2):
    """
    Merges two sorted linked lists into one sorted list.

    Args:
        list1: The head of the first linked list.
        list2: The head of the second linked list.

    Returns:
        The head of the merged sorted linked list.
    """
    dummy = ListNode()
    tail = dummy

    while list1 and list2:
        if list1.val <= list2.val:
            tail.next = list1
            list1 = list1.next
        else:
            tail.next = list2
            list2 = list2.next
        tail = tail.next

    if list1:
        tail.next = list1
    elif list2:
        tail.next = list2

    return dummy.next

# Example usage (assuming you have a function to create a linked list)
list1 = create_linked_list([1, 2, 4])
list2 = create_linked_list([1, 3, 4])
merged_list = merge_two_lists(list1, list2)
# Print the merged list (implementation of printing depends on your ListNode class)
```

* **Explanation:**
    * Create a dummy node to simplify the logic.
    * Initialize a `tail` pointer to the dummy node.
    * Iterate through both lists:
        * Compare the values of the current nodes in `list1` and `list2`.
        * Append the node with the smaller value to the `tail` and move the corresponding pointer forward.
    * If one list becomes empty, append the remaining nodes of the other list to the `tail`.
    * Return the head of the merged list (the next node of the dummy node).

**5. Longest Substring Without Repeating Characters**

* **Problem:** Find the length of the longest substring without repeating characters.

* **Python Code:**

```python
def length_of_longest_substring(s):
    """
    Finds the length of the longest substring without repeating characters.

    Args:
        s: The input string.

    Returns:
        The length of the longest substring.
    """
    char_index = {}  # Dictionary to store the last seen index of each character
    max_length = 0
    start = 0

    for end in range(len(s)):
        if s[end] in char_index and char_index[s[end]] >= start:
            start = char_index[s[end]] + 1
        char_index[s[end]] = end
        max_length = max(max_length, end - start + 1)

    return max_length

# Example usage
s = "abcabcbb"
result = length_of_longest_substring(s)
print(result)  # Output: 3 (Longest substring is "abc")
```

* **Explanation:**
    * Use a sliding window approach.
    * Maintain a dictionary `char_index` to store the last seen index of each character.
    * Iterate through the string:
        * If the current character is already in the `char_index` and its last seen index is within the current window (i.e., greater than or equal to the `start` of the window), update the `start` of the window to the next index after the last occurrence of the character.
        * Update the `char_index` with the current index of the character.
        * Update the `max_length` if the current window size is greater.



**6. Climbing Stairs**

* **Problem:** You are climbing a staircase. It takes `n` steps to reach the top. Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

* **Python Code:**

```python
def climb_stairs(n):
    """
    Calculates the number of distinct ways to climb n stairs.

    Args:
        n: The number of stairs.

    Returns:
        The number of distinct ways to climb the stairs.
    """
    if n <= 1:
        return 1
    dp = [0] * (n + 1)  # Create a dynamic programming array
    dp[0] = 1
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]
    return dp[n]

# Example usage
n = 5
result = climb_stairs(n)
print(result)  # Output: 8
```

* **Explanation:**
    * This problem can be solved using dynamic programming.
    * Create a `dp` array to store the number of ways to reach each step.
    * Initialize `dp[0]` and `dp[1]` to 1 (base cases).
    * Iterate from step 2 to `n`:
        * The number of ways to reach step `i` is the sum of ways to reach step `i-1` and step `i-2`.
    * Return the number of ways to reach step `n` (stored in `dp[n]`).

**7. Binary Search**

* **Problem:** Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write an efficient algorithm that searches for `target` in `nums`. If `target` is found, return its index. Otherwise, return `-1`.

* **Python Code:**

```python
def binary_search(nums, target):
    """
    Performs binary search on a sorted array.

    Args:
        nums: A sorted list of integers.
        target: The target value to search for.

    Returns:
        The index of the target if found, otherwise -1.
    """
    left = 0
    right = len(nums) - 1

    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1

# Example usage
nums = [-1, 0, 3, 5, 9, 12]
target = 9
result = binary_search(nums, target)
print(result)  # Output: 4
```

* **Explanation:**
    * Initialize `left` and `right` pointers to the beginning and end of the array, respectively.
    * While `left` is less than or equal to `right`:
        * Calculate the `mid` index.
        * If `nums[mid]` is equal to the `target`, return the `mid` index.
        * If `nums[mid]` is less than the `target`, update `left` to `mid + 1`.
        * If `nums[mid]` is greater than the `target`, update `right` to `mid - 1`.
    * If the loop completes without finding the `target`, return `-1`.



**8. Implement Queue using Stacks**

* **Problem:** Implement a first-in, first-out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a standard queue (`push`, `pop`, `peek`, `empty`).

* **Python Code:**

```python
class MyQueue:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.stack1 = []  # For enqueue operations
        self.stack2 = []  # For dequeue operations

    def push(self, x: int) -> None:
        """
        Push element x to the back of queue.
        """
        self.stack1.append(x)

    def pop(self) -> int:
        """
        Removes the element from in front of queue and returns that element.
        """
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        return self.stack2.pop()

    def peek(self) -> int:
        """
        Gets the element at the front of the queue.
        """
        if not self.stack2:
            while self.stack1:
                self.stack2.append(self.stack1.pop())
        return self.stack2[-1]

    def empty(self) -> bool:
        """
        Returns whether the queue is empty.
        """
        return not self.stack1 and not self.stack2

# Example usage
queue = MyQueue()
queue.push(1)
queue.push(2)
print(queue.peek())  # Output: 1
print(queue.pop())   # Output: 1
print(queue.empty())  # Output: False

```

* **Explanation:**
    * We use two stacks:
        * `stack1`: Primarily used for `push` operations.
        * `stack2`: Primarily used for `pop` and `peek` operations.
    * `push(x)`: Simply append `x` to `stack1`.
    * `pop()`: 
        * If `stack2` is empty, transfer all elements from `stack1` to `stack2` (reversing the order).
        * Pop and return the top element from `stack2`.
    * `peek()`:
        * If `stack2` is empty, transfer all elements from `stack1` to `stack2`.
        * Return the top element of `stack2`.
    * `empty()`: Return `True` if both `stack1` and `stack2` are empty.

**9. Valid Palindrome**

* **Problem:** Determine whether a given string is a palindrome.

* **Python Code:**

```python
def is_palindrome(s):
    """
    Checks if a string is a palindrome.

    Args:
        s: The input string.

    Returns:
        True if the string is a palindrome, False otherwise.
    """
    left = 0
    right = len(s) - 1

    while left < right:
        while left < right and not alphanum(s[left]):
            left += 1
        while left < right and not alphanum(s[right]):
            right -= 1
        if s[left].lower() != s[right].lower():
            return False
        left += 1
        right -= 1

    return True

def alphanum(c):
    """
    Checks if a character is alphanumeric.
    """
    return (ord('a') <= ord(c) <= ord('z') or
            ord('A') <= ord(c) <= ord('Z') or
            ord('0') <= ord(c) <= ord('9'))

# Example usage
s1 = "A man, a plan, a canal: Panama"
s2 = "race a car"
print(is_palindrome(s1))  # Output: True
print(is_palindrome(s2))  # Output: False
```

* **Explanation:**
    * Initialize `left` and `right` pointers to the beginning and end of the string, respectively.
    * While `left` is less than `right`:
        * Move `left` to the next alphanumeric character.
        * Move `right` to the previous alphanumeric character.
        * Compare the characters at `left` and `right` (ignoring case). If they are not equal, return `False`.
    * If the loop completes without finding any mismatches, return `True`.


**10. Merge Sorted Array**

* **Problem:** Given two sorted integer arrays `nums1` and `nums2`, merge `nums2` into `nums1` in such a way that it becomes a single, sorted array.

* **Python Code:**

```python
def merge(nums1, m, nums2, n):
    """
    Merges two sorted arrays into one.

    Args:
        nums1: The first array.
        m: The number of elements in nums1.
        nums2: The second array.
        n: The number of elements in nums2.

    Modifies nums1 in-place to contain the merged sorted array.
    """
    p1 = m - 1  # Pointer for nums1
    p2 = n - 1  # Pointer for nums2
    p = m + n - 1  # Pointer for the merged array

    while p2 >= 0:
        if p1 >= 0 and nums1[p1] > nums2[p2]:
            nums1[p] = nums1[p1]
            p1 -= 1
        else:
            nums1[p] = nums2[p2]
            p2 -= 1
        p -= 1

# Example usage
nums1 = [1, 2, 3, 0, 0, 0]
m = 3
nums2 = [2, 5, 6]
n = 3
merge(nums1, m, nums2, n)
print(nums1)  # Output: [1, 2, 2, 3, 5, 6]
```

* **Explanation:**
    * Initialize pointers `p1`, `p2`, and `p` as described above.
    * Compare `nums1[p1]` and `nums2[p2]`:
        * If `nums1[p1]` is greater than `nums2[p2]`, place `nums1[p1]` at `nums1[p]`.
        * Otherwise, place `nums2[p2]` at `nums1[p]`.
    * Decrement the appropriate pointers (`p1` or `p2`) and the main pointer `p`.
    * Continue until `p2` reaches 0.

**11. Remove Duplicates from Sorted Array**

* **Problem:** Given an integer array `nums` sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

* **Python Code:**

```python
def remove_duplicates(nums):
    """
    Removes duplicates from a sorted array.

    Args:
        nums: The input array.

    Returns:
        The length of the array after removing duplicates.
    """
    if not nums:
        return 0

    slow = 0
    for fast in range(1, len(nums)):
        if nums[slow] != nums[fast]:
            slow += 1
            nums[slow] = nums[fast]

    return slow + 1

# Example usage
nums = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
length = remove_duplicates(nums)
print(nums[:length])  # Output: [0, 1, 2, 3, 4]
```

* **Explanation:**
    * Initialize `slow` and `fast` pointers.
    * Iterate through the array:
        * If `nums[slow]` is different from `nums[fast]`, increment `slow` and place `nums[fast]` at `nums[slow]`.
    * Return `slow + 1` as the length of the array after removing duplicates.

**12. String to Integer (atoi)**

* **Problem:** Implement the `myAtoi(string s)` function, which converts a string to an integer.

* **Python Code:**

```python
def my_atoi(s):
    """
    Converts a string to an integer.

    Args:
        s: The input string.

    Returns:
        The integer value of the string.
    """
    s = s.strip()
    if not s:
        return 0

    sign = 1
    if s[0] == '-':
        sign = -1
        s = s[1:]
    elif s[0] == '+':
        s = s[1:]

    result = 0
    for char in s:
        if not char.isdigit():
            break
        result = result * 10 + int(char)
        if result > 2**31 - 1:
            return 2**31 - 1
        if result < -2**31:
            return -2**31

    return result * sign

# Example usage
s = "42"
print(my_atoi(s))  # Output: 42
s = "   -42"
print(my_atoi(s))  # Output: -42
s = "4193 with words"
print(my_atoi(s))  # Output: 4193
s = "words and 987"
print(my_atoi(s))  # Output: 0
```

* **Explanation:**
    * Remove leading and trailing whitespaces.
    * Handle the sign (positive or negative).
    * Iterate through the characters:
        * If the character is not a digit, break the loop.
        * Convert the digit to an integer and add it to the `result`.
        * Check for integer overflow/underflow.
    * Return the `result` multiplied by the `sign`.

**13. Longest Common Prefix**

* **Problem:** Write a function to find the longest common prefix string amongst an array of strings.

* **Python Code:**

```python
def longest_common_prefix(strs):
    """
    Finds the longest common prefix among an array of strings.

    Args:
        strs: The array of strings.

    Returns:
        The longest common prefix.
    """
    if not strs:
        return ""

    prefix = strs[0]
    for i in range(1, len(strs)):
        while not strs[i].startswith(prefix):
            prefix = prefix[:-1]
            if not prefix:
                return ""

    return prefix

# Example usage
strs = ["flower", "flow", "flight"]
print(longest_common_prefix(strs))  # Output: "fl"
```

* **Explanation:**
    * Initialize `prefix` to the first string in the array.
    * Iterate through the remaining strings:
        * While the current string does not start with the `prefix`, shorten the `prefix` by one character.
        * If the `prefix` becomes empty, return an empty string.
    * Return the final `prefix`.

**14. Roman to Integer**

* **Problem:** Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D`, and `M`. Given a roman numeral, convert it to an integer.

* **Python Code:**

```python
def roman_to_integer(s):
    """
    Converts a Roman numeral to an integer.

    Args:
        s: The Roman numeral string.

    Returns:
        The integer value of the Roman numeral.
    """
    roman_map = {'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000}
    result = 0
    prev_val = 0

    for char in s[::-1]:
        curr_val = roman_map[char]
        if curr_val < prev_val:
            result -= curr_val
        else:
            result += curr_val
        prev_val = curr_val

    return result

# Example usage
s = "III"
print(roman_to_integer(s))  # Output: 3
s = "IV"
print(roman_to_integer(s))  # Output: 4
s = "IX"
print(roman_to_integer(s))  # Output: 9
s = "LVIII"
print(roman_to_integer(s))  # Output: 58
s = "MCMXCIV"
print(roman_to_integer(s))  # Output: 1994
```

* **Explanation:**
    * Create a dictionary `roman_map` to store the integer values of Roman numerals.
    * Iterate through the Roman numeral string in reverse order:
        * If the current value is less than the previous value, subtract the current value from the `result`.
        * Otherwise, add the current value to the `result

**15. Container With Most Water**

* **Problem:** Given an integer array `height` of length `n`, where `height[i]` is the height of the `i`-th line on the x-axis, find two lines that together with the x-axis form a container, such that the container contains the most water.

* **Python Code:**

```python
def max_area(height):
    """
    Finds the container with the most water.

    Args:
        height: An array of integers representing the height of each line.

    Returns:
        The maximum area of the container.
    """
    left = 0
    right = len(height) - 1
    max_area = 0

    while left < right:
        area = min(height[left], height[right]) * (right - left)
        max_area = max(max_area, area)

        if height[left] < height[right]:
            left += 1
        else:
            right -= 1

    return max_area

# Example usage
height = [1, 8, 6, 2, 5, 4, 8, 3, 7]
print(max_area(height))  # Output: 49
```

* **Explanation:**
    * Initialize `left` and `right` pointers to the beginning and end of the array.
    * Calculate the area of the container formed by the current `left` and `right` pointers.
    * Update `max_area` if the current area is greater.
    * Move the pointer with the shorter height inward (to potentially increase the area).
    * Repeat until `left` and `right` pointers meet.

**16. 3Sum**

* **Problem:** Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

* **Python Code:**

```python
def three_sum(nums):
    """
    Finds all unique triplets that sum to zero.

    Args:
        nums: The input array.

    Returns:
        A list of all unique triplets.
    """
    nums.sort()
    result = []

    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i - 1]:
            continue
        left = i + 1
        right = len(nums) - 1

        while left < right:
            sum_three = nums[i] + nums[left] + nums[right]
            if sum_three == 0:
                result.append([nums[i], nums[left], nums[right]])
                while left < right and nums[left] == nums[left + 1]:
                    left += 1
                while left < right and nums[right] == nums[right - 1]:
                    right -= 1
                left += 1
                right -= 1
            elif sum_three < 0:
                left += 1
            else:
                right -= 1

    return result

# Example usage
nums = [-1, 0, 1, 2, -1, -4]
print(three_sum(nums))  # Output: [[-1, -1, 2], [-1, 0, 1]]
```

* **Explanation:**
    * Sort the `nums` array.
    * Iterate through the array using the `i` pointer:
        * Skip duplicate values for `nums[i]`.
        * Initialize `left` and `right` pointers.
        * While `left` is less than `right`:
            * Calculate the sum of `nums[i]`, `nums[left]`, and `nums[right]`.
            * If the sum is 0, add the triplet to the `result` and skip duplicate values for `nums[left]` and `nums[right]`.
            * If the sum is less than 0, move the `left` pointer to the right.
            * If the sum is greater than 0, move the `right` pointer to the left.
    * Return the list of triplets.

**17. Letter Combinations of a Phone Number**

* **Problem:** Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

* **Python Code:**

```python
def letter_combinations(digits):
    """
    Finds all possible letter combinations of a phone number.

    Args:
        digits: The string of digits.

    Returns:
        A list of all possible letter combinations.
    """
    if not digits:
        return []

    digit_to_letters = {
        '2': 'abc',
        '3': 'def',
        '4': 'ghi',
        '5': 'jkl',
        '6': 'mno',
        '7': 'pqrs',
        '8': 'tuv',
        '9': 'wxyz'
    }

    def backtrack(index, current_string):
        if index == len(digits):
            combinations.append(current_string)
            return

        for letter in digit_to_letters[digits[index]]:
            backtrack(index + 1, current_string + letter)

    combinations = []
    backtrack(0, '')
    return combinations

# Example usage
digits = "23"
print(letter_combinations(digits))  # Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"]
```

* **Explanation:**
    * Create a dictionary `digit_to_letters` to map digits to their corresponding letters.
    * Use backtracking to explore all possible combinations.
        * The `backtrack` function recursively explores each digit and adds its corresponding letters to the `current_string`.
        * When the `index` reaches the end of the `digits` string, add the `current_string` to the `combinations` list.

**18. Combination Sum**

* **Problem:** Given an array of distinct integers `candidates` and a target integer `target`, return a list of all unique combinations of `candidates` where the numbers in each combination add up to `target`. You may return the combinations in any order.

* **Python Code:**

```python
def combination_sum(candidates, target):
    """
    Finds all unique combinations of candidates that sum to the target.

    Args:
        candidates: An array of distinct integers.
        target: The target sum.

    Returns:
        A list of all unique combinations.
    """
    result = []

    def backtrack(index, current, total):
        if total == target:
            result.append(list(current))
            return

        if total > target or index >= len(candidates):
            return

        current.append(candidates[index])
        backtrack(index, current, total + candidates[index])
        current.pop()  # Backtrack
        backtrack(index + 1, current, total)

    backtrack(0, [], 0)
    return result

# Example usage
candidates = [2, 3, 6, 7]
target = 7
print(combination_sum(candidates, target))  # Output: [[2, 2, 3], [7]]
```

* **Explanation:**
    * Use backtracking to explore all possible combinations.
        * The `backtrack` function recursively explores each candidate:
            * If the `total` reaches the `target`, add the `current` combination to the `result`.
            * If the `total` exceeds the `target` or the `index` exceeds the bounds, stop the recursion.
            * Include the current `candidate` in the `current` combination and recursively explore further.
            * Backtrack by removing the current `candidate` from the `current` combination.
            * Explore the next `candidate` without including the current one.


**19. Permutations**

* **Problem:** Given an array `nums` of distinct integers, return all the possible permutations. You can return the answer in any order.

* **Python Code:**

```python
def permute(nums):
    """
    Finds all permutations of an array.

    Args:
        nums: The input array.

    Returns:
        A list of all permutations.
    """
    result = []

    def backtrack(current_permutation):
        if len(current_permutation) == len(nums):
            result.append(list(current_permutation))
            return

        for num in nums:
            if num not in current_permutation:
                current_permutation.append(num)
                backtrack(current_permutation)
                current_permutation.pop()

    backtrack([])
    return result

# Example usage
nums = [1, 2, 3]
print(permute(nums))  # Output: [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
```

* **Explanation:**
    * Use backtracking to explore all possible permutations.
        * The `backtrack` function recursively explores each number in the `nums` array:
            * If the `current_permutation` has the same length as `nums`, add it to the `result`.
            * If the `num` is not already in the `current_permutation`, add it to the `current_permutation` and recursively explore further.
            * Backtrack by removing the `num` from the `current_permutation`.

**20. Subsets**

* **Problem:** Given an integer array `nums`, return all possible subsets (the power set). The solution must not contain duplicate subsets.

* **Python Code:**

```python
def subsets(nums):
    """
    Finds all subsets of an array.

    Args:
        nums: The input array.

    Returns:
        A list of all subsets.
    """
    result = [[]]

    for num in nums:
        new_subsets = [subset + [num] for subset in result]
        result.extend(new_subsets)

    return result

# Example usage
nums = [1, 2, 3]
print(subsets(nums))  # Output: [[], [1], [2], [1, 2], [3], [1, 3], [2, 3], [1, 2, 3]]
```

* **Explanation:**
    * Start with an empty set (an empty list) in the `result`.
    * Iterate through each number in `nums`:
        * Create new subsets by adding the current `num` to each existing subset in the `result`.
        * Add the new subsets to the `result`.



**Explanation:**
- Binary search works by dividing the search space into halves.
- Initialize `left` to 0 and `right` to the last index of the array.
- Compute the middle index `mid` and compare `nums[mid]` with `target`:
  - If `nums[mid] == target`, return `mid` as the index of the target.
  - If `nums[mid] < target`, move `left` to `mid + 1` to search in the right half.
  - If `nums[mid] > target`, move `right` to `mid - 1` to search in the left half.
- If the `target` is not found, return `-1`.

---

## Usage

Each code snippet includes a sample usage example. To run the code:
1. Copy the Python code into your development environment (e.g., VSCode, PyCharm, or Jupyter Notebook).
2. Replace sample inputs with your custom test cases as needed.
3. Execute the code and verify the results.

## Contribution

If you'd like to contribute to this repository:
1. Fork the repository.
2. Create a new branch: `git checkout -b feature/new-feature`.
3. Make your changes and commit them: `git commit -m "Add new feature"`.
4. Push to the branch: `git push origin feature/new-feature`.
5. Submit a pull request.

---

Feel free to ask for more algorithm explanations or additional features! 😊

