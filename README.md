# Leetcode
This is a notebook for leetcode learning. :smiley:
## Chapters
### Array
- Binary Search

| Problems | Summary | Times | Others |
| -------- | ------- | ----- | ------ |
| [704. Binary Search](https://leetcode.com/problems/binary-search/) | 基本操作:边界&循环条件；```mid=left+(right-left)/2;(防止溢出) ```| 1 | |
| [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/) | ```insert position(when left==right): left/right+1```| 1 | |
| [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)| | | ⭐ |
|[69. Sqrt(x)](https://leetcode.cn/problems/sqrtx/)|
|[367. Valid Perfect Square](https://leetcode.cn/problems/valid-perfect-square/)|

- Remove Element
双指针法（快慢指针法）
时间复杂度O(n) 空间复杂度O(1)

| Problems | Summary | Times | Others |
| ---| --- | --- | --- |
|[27. Remove Element](https://leetcode.com/problems/remove-element/)| ```if(val!=nums[fastIndex]) nums[slowIndex++]=nums[fastIndex]``` |
|[26. Remove Duplicates from Sorted Array](https://leetcode.cn/problems/remove-duplicates-from-sorted-array/)|
|[283. Move Zeroes](https://leetcode.cn/problems/move-zeroes/)|
|[844. Backspace String Compare](https://leetcode.cn/problems/backspace-string-compare/) | | | ⭐ |
|[977. Squares of a Sorted Array](https://leetcode.cn/problems/squares-of-a-sorted-array/)|

- :o:**Silding Window**
(two pointers)

O(n) 


| Problems | Summary | Times | Others |
| ---| --- | --- | --- |
|[209. Minimum Size Subarray Sum](https://leetcode.cn/problems/minimum-size-subarray-sum/)|一个for循环，窗口起始位置移动规则```while(sum>=target){sum-=nums[i++];}```|| :star: |
|[904. Fruit Into Baskets](https://leetcode.cn/problems/fruit-into-baskets/)|求最大，移动条件：type>2（不满足条件的时候）|| ⭐|
|[76. Minimum Window Substring](https://leetcode.cn/problems/minimum-window-substring/)|```for(const auto &p:mpt)``` 记录start|





