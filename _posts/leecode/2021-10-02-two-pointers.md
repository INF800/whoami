---
title: Two Pointers
updated: 2021-10-02 23:37
category: 
- dsa
---


## List of two pointer problems

[^0]: Container with most water
[^1]: Two sum II
[^2]: Two sum III(### 1. Two sum II)


<div class="divider"></div>


### 1. Two sum II

[Leetcode Link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

- The main idea is that there is only one solution (pair of of target sum). 
- If you start from left and right and check the sum, eventually you will stumble across the pairs.
- Updating pointers is easy because array is sorted. Updating left/right increases/decreases sum as array is sorted. 
- The increase/decreases will never overshoot the solution because array is sorted.

