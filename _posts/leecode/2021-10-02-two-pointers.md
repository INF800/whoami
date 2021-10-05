---
title: Two Pointers
updated: 2021-10-02 23:37
category: 
- dsa
---


## List of two pointer problems

1. Container with most water
2. Two sum II
3. Three sum

<div class="divider"></div>

### 1. Container with most water

```java
// todo
```

<div class="divider"></div>

### 2. Two sum II

[Leetcode Link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

- The main idea is that there is only one solution (pair of of target sum). 
- If you start from left and right and check the sum, eventually you will stumble across the pairs.
- Updating pointers is easy because array is sorted. Updating left/right increases/decreases sum as array is sorted. 
- The increase/decreases will never overshoot the solution because array is sorted.

```java
// Runtime: 1 ms, faster than 58.31% of Java online submissions for Two Sum II - Input array is sorted.
// Memory Usage: 41.4 MB, less than 28.48% of Java online submissions for Two Sum II - Input array is sorted.

import java.lang.*;

class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int[] pairs = {0, 0};
        int l = 0;
        int r = numbers.length-1;
        
        while (l<r){
            int sum = numbers[l]+numbers[r];
            if (sum==target){
                pairs[0] = l+1; // 1-indexed
                pairs[1] = r+1; // 1-indexed
                return pairs;
            }
            
            // update rule
            if (sum<target){
                l++;
            } else if (sum>target){
                r--;
            }
        }
        
        return pairs;
    }
}
```

<div class="divider"></div>

### 2. Three sum

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        Arrays.sort(nums);
        for (int i = 0; i + 2 < nums.length; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) {            
                continue;
            }
            int j = i + 1, k = nums.length - 1;  
            int target = -nums[i];
            while (j < k) {
                if (nums[j] + nums[k] == target) {
                    res.add(Arrays.asList(nums[i], nums[j], nums[k]));
                    j++;
                    k--;
                    while (j < k && nums[j] == nums[j - 1]) j++;  
                    while (j < k && nums[k] == nums[k + 1]) k--;  
                } else if (nums[j] + nums[k] > target) {
                    k--;
                } else {
                    j++;
                }
            }
        }
        return res;
    }
}
```

<div class="divider"></div>
