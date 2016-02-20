---
layout: post
title: LeetCode - Convert Sorted Array to Binary Search Tree
description: "LeetCode"
tags: [LeetCode,code]
date: 2015-7-18
---

> Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

这道题思路有点像二分查找。

```c
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
struct TreeNode* sortedArrayToBST(int* nums, int numsSize) {
    if(numsSize == 0)
        return NULL;
    struct TreeNode *Root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
    Root->val = *(nums + numsSize / 2);
    Root->left = sortedArrayToBST(nums, numsSize / 2);
    Root->right = sortedArrayToBST(nums + numsSize / 2 + 1, numsSize-numsSize/2-1);
    return Root;
}
```

