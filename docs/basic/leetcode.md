?> ![](https://notes.abelsu7.top/_media/leetcode.png ':size=16')Leetcode 题解

## 1. Two Sum

!> Return indices of the two numbers.

### Question

> Given an array of integers, **return indices of the two numbers** such that they **add up to a specific target**. [![](https://notes.abelsu7.top/_media/leetcode.png ':size=16')See it on Leetcode](https://leetcode-cn.com/problems/two-sum/)

```bash
For example:
Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
It should return [0, 1].
```

### Hint

> You may assume that each input would have **exactly one solution**.

### Solution #1 Brute Force - 38ms / 59ms

<!-- tabs:start -->

#### **java**

```java
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{0, 0}; 
    }
}
```

#### **go**

```go
func twoSum(nums []int, target int) []int {
    for i := 0; i < len(nums) - 1; i++ {
        for j := i + 1; j < len(nums); j++ {
            if nums[i] + nums[j] == target {
                return []int{i, j}
            }
        }
    }
    return []int{0, 0}
}
```
<!-- tabs:end -->

### Solution #2 One-pass Hash Table - 7ms / 9ms

<!-- tabs:start -->
#### **Java**

```java
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i};
            }
            map.put(nums[i], i);
        }
        throw new IllegalArgumentException("No two sum solution"); 
    }
}
```
#### **Go**

```go
func twoSum(nums []int, target int) []int {
    m := make(map[int]int)
    for i := range nums {
        complement := target - nums[i]
        elem, ok := m[complement]
        if ok {
            return []int{elem, i}
        }
        m[nums[i]] = i
    }
    return []int{0, 0}
}
```
<!-- tabs:end -->

## 11. Container With Most Water

!> Find a container which contains the most water.

### Question

> Given **n non-negative integers** `a1, a2, ..., an`, where each represents a point at coordinate `(i, ai)`. n vertical lines are drawn such that the two endpoints of line i is at `(i, ai)` and `(i, 0)`. Find two lines, which **together with x-axis forms a container**, such that the container **contains the most water**. [![](https://notes.abelsu7.top/_media/leetcode.png ':size=16')See it on Leetcode](https://leetcode-cn.com/problems/container-with-most-water/)

### Note

> 1. You may not slant the container.
> 2. Brute Force approach may cause **TLE**.

![Two Pointer Approach](https://notes.abelsu7.top/_images/leetcode-11.gif)

### Solution in Brute Force - TLE

```java
public class Solution {
    public int maxArea(int[] height) {
        int n = height.length, maxArea = 0;
        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                maxArea = Math.max((j - i) * Math.min(height[i], height[j]), maxArea);
            }
        }
        return maxArea;
    }
}
```

### Solution in Java, C++ and Go

<!-- tabs:start -->
#### **Java**

```java
public class Solution {
    public int maxArea(int[] height) {
        int maxArea = 0;
        int l = 0, r = height.length - 1;
        while (l < r) {
            maxArea = Math.max(maxArea, Math.min(height[l], height[r]) * (r - l));
            if (height[l] < height[r]) {
                l++;
            } else {
                r--;
            }
        }
        return maxArea;
    }
}
```

#### **C++**

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int maxArea = 0;
        int l = 0, r = height.size() - 1;
        while (l < r) {
            maxArea = fmax(maxArea, fmin(height[l], height[r]) * (r - l));
            if (height[l] < height[r]) {
                l++;
            } else {
                r--;
            }
        }
        return maxArea; 
    }
};
```

#### **Go**

```go
func maxArea(height []int) int {
    var maxArea, l, r int = 0, 0, len(height) - 1
    for l < r {
        switch {
        case height[l] < height[r]:
            if height[l] * (r - l) > maxArea {
                maxArea = height[l] * (r - l)
            }
        default:
            if height[r] * (r - l) > maxArea {
                maxArea = height[r] * (r - l)
            }
        }
        if height[l] < height[r] {
            l++
        } else {
            r--
        }
    }
    return maxArea
}
```
<!-- tabs:end -->

## 83. Remove Duplicates from Sorted List

!> Delete all duplicates in a sorted linked list.

### Question

> Given a **sorted linked list**, **delete all duplicates** such that each element appear only once. [![](https://notes.abelsu7.top/_media/leetcode.png ':size=16')See it on Leetcode](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)

```bash
For example,
Given "1->1->2", return "1->2".
Given "1->1->2->3->3", return "1->2->3".
```

### Hint

> This is a simple problem that merely tests your ability to **manipulate list node pointers**. Because the input list is sorted, **we can determine if a node is a duplicate by comparing its value to the node after it in the list**. If it is a duplicate, we change the `next` pointer of the current node so that **it skips the next node and points directly to the one after the next node**.

### Solution

<!-- tabs:start --->
#### **Java**

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode current = head;
        while (current != null && current.next != null) {
            if (current.next.val == current.val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }
        return head;
    }
}
```

#### **C++**

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode* current = head;
        while(current != NULL && current->next != NULL) {
            if (current->val == current->next->val) {
                current->next = current->next->next;
            } else {
                current = current->next;
            }
        }
        return head;
    }
};
```

<!-- tabs:end -->

## 121. Best Time to Buy and Sell Stock

!> Design an algorithm to find the maximum profit.

### Question

> Say you have an array for which the ith element is the price of a given stock on day i. If you were only permitted to complete **at most one transaction** (ie, buy one and sell one share of the stock), design an algorithm to **find the maximum profit**. [![](https://notes.abelsu7.top/_media/leetcode.png ':size=16')See it on Leetcode](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/)

### Example 1

```
Input: [7, 1, 5, 3, 6, 4]
Output: 5
max. difference = 6-1 = 5 
Not 7-1 = 6, as selling price needs to be larger than buying price.
```

### Example 2

```
Input: [7, 6, 4, 3, 1]
Output: 0
In this case, no transaction is done, i.e. max profit = 0.
```

### Hint

> Brute force approach may result in **Time Limit Exceeded**. Try **greedy approach**.

### Solution in Java and Go

<!-- tabs:start -->

#### **Java**

```java
public class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;
        for (int i : prices) {
            if (i < minPrice) {
                minPrice = i;
            } else if (i - minPrice > maxProfit) {
                maxProfit = i - minPrice;
            }
        }
        return maxProfit;
    }
}
```

#### **Go**

```go
func maxProfit(prices []int) int {
    if len(prices) == 0 {
        return 0
    }
    minPrice := prices[0]
    profit := 0
    for _, values := range prices {
        switch  {
        case values < minPrice:
            minPrice = values
        case values - minPrice > profit:
            profit = values - minPrice
        }
    }
    return profit
}
```
<!-- tabs:end -->

## 136. Single Number

!> Find the single integer.

### Question

> Given an array of integers, **every element appears twice except for one**. Find that single one. [![](https://notes.abelsu7.top/_media/leetcode.png ':size=16')See it on Leetcode](https://leetcode-cn.com/problems/single-number/)

### Example

```
Given int[] arr = {1, 2, 1, 3, 4, 3, 2}, 
it should return 4.
```

### Hint

> Your algorithm should have a **linear runtime complexity**. Could you implement it **without using extra memory**?

### Solution in Java and C++

<!--  tabs:start -->
#### **Java**
```java
public class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for (int i:nums){
            result ^= i;
        }
        return result;
    }
}
```

#### **C++**
```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int result = 0;
        for (int i = 0; i < nums.size(); i++) {
            result ^= nums[i];
        }
        return result;
    }
};
```
<!--  tabs:end -->

## 137. Single Number II

!> Find the single integer II.

### Question

> Given an array of integers, **every element appears three times except for one**. Find that single one. [![](https://notes.abelsu7.top/_media/leetcode.png ':size=16')See it on Leetcode](https://leetcode-cn.com/problems/single-number-ii/)

### Example

```
Given int[] arr = {1, 2, 1, 1, 3, 4, 3, 3, 2, 2}, 
it should return 4.
```

### Hint

> Your algorithm should have a **linear runtime complexity**. Could you implement it **without using extra memory**?

### Solution in Java and C++

<!--  tabs:start -->
#### **Java**
```java
public class Solution {
    public int singleNumber(int[] nums) {
        int one = 0, two = 0;
        for (int i = 0; i < nums.length; i++) {
            two |= nums[i] & one;
            one ^= nums[i];
            int three = one & two;
            one &= ~three;
            two &= ~three;
        }
        return one;
    }
}}
```

#### **C++**
```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int one = 0, two = 0;  
        for (int i = 0; i < nums.size() ; i++)  
        {  
            two |= nums[i] & one;  
            one ^= nums[i];  
            int three = one & two;  
            one &= ~three;  
            two &= ~three;  
        }  
        return one;
    }
};
```
<!--  tabs:end -->

## 167. Two Sum II - Input array is sorted

!> Return indices of the two numbers added up to the target.

### Question

> Given an array of integers that is already **sorted in ascending order**, find two numbers such that they add up to a specific target number. [![](https://notes.abelsu7.top/_media/leetcode.png ':size=16')See it on Leetcode](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/)

### Example

```
Given input numbers = [2, 7, 11, 15], with target = 9,
it should return [1, 2].
```

### Hint

> 1. The function twoSum should return indices of the two numbers such that they add up to the target, where **index1 must be less than index2**.
> 2. Your returned answers (both index1 and index2) are **not zero-based**.
> 3. Each input would have **exactly one solution**.

### Solution in Java and Go

<!--  tabs:start -->
#### **Java**
```java
public class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int left = 0, right = numbers.length - 1;
        while (left < right) {
            if (numbers[left] + numbers[right] == target) {
                return new int[]{left + 1, right + 1};
            } else if (numbers[left] + numbers[right] < target) {
                left++;
            } else {
                right--;
            }
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}
```

#### **Go**
```go
func twoSum(numbers []int, target int) []int {
    left := 0
    right := len(numbers) - 1
    for left < right {
        switch {
        case numbers[left] + numbers[right] > target:
            right--
        case numbers[left] + numbers[right] < target:
            left++
        default:
            return []int{left + 1, right + 1}
        }
    }
    return []int{0, 0}
}
```

<!-- tabs:end -->

### Solution in C++ and JavaScript
 
<!-- tabs:start -->

#### **C++**
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        vector<int> ans;
        int left = 0, right = numbers.size() - 1;
        while (left < right) {
            if (numbers[left] + numbers[right] == target) {
                ans.push_back(left + 1);
                ans.push_back(right + 1);
                return ans;
            } else if (numbers[left] + numbers[right] > target) {
                right--;
            } else {
                left++;
            }
        }
        return ans;
    }
};
```

#### **JavaScript**
```js
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(numbers, target) {
    var left = 0, right = numbers.length - 1;
    while (left < right) {
        if (numbers[left] + numbers[right] == target) {
            return new Array(left + 1, right + 1);
        } else if (numbers[left] + numbers[right] < target) {
            left++;
        } else {
            right--;
        }
    }
    return new Array(0, 0);
};
```
<!--  tabs:end -->