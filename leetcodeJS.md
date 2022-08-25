1. 两数之和  
给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。  
你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。  
你可以按任意顺序返回答案。

> 示例 1：
输入：nums = [2,7,11,15], target = 9
输出：[0,1]
解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。

> 示例 2：
输入：nums = [3,2,4], target = 6
输出：[1,2]

> 示例 3：
输入：nums = [3,3], target = 6
输出：[0,1]
 

> 提示：  
2 <= nums.length <= 104  
-109 <= nums[i] <= 109  
-109 <= target <= 109  
只会存在一个有效答案 

进阶：你可以想出一个时间复杂度小于 O(n2) 的算法吗？
```js
/**
    @param {number[]} nums
    @param {number} target
    @return {number[]}
 */

var twoSum = (nums, target) => {
    let hash = {}
    for (let i = 0; i < nums.length; i++) {
        if (hash[target - nums[i]] !== undefined) {
            return [i, hash[target - nums[i]]]
        } else {
            hash[nums[i]] = i
        }
    }
    return []
}
```
2. 两数相加  
给你两个 非空 的链表，表示两个非负的整数。它们每位数字都是按照 逆序 的方式存储的，并且每个节点只能存储 一位 数字。  
请你将两个数相加，并以相同形式返回一个表示和的链表。  
你可以假设除了数字 0 之外，这两个数都不会以 0 开头。

> 示例 1：
输入：l1 = [2,4,3], l2 = [5,6,4]
输出：[7,0,8]
解释：342 + 465 = 807.

> 示例 2：
输入：l1 = [0], l2 = [0]
输出：[0]

> 示例 3：
输入：l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
输出：[8,9,9,9,0,0,0,1]
 

> 提示：
每个链表中的节点数在范围 [1, 100] 内
0 <= Node.val <= 9
题目数据保证列表表示的数字不含前导零

```js
/**
    Definition singly-linked list.
    function ListNode(val, next) {
        this.val = val === undefined ? null : val
        this.next = next === undefined ? 0 : next
    }
 */
/**
    @param {ListNode} l1
    @param {ListNode} l2
    @return {ListNode}
 */

const addTwoNumbers = (l1, l2) => {
    let head = null, tail = null, carry = 0
    while(l1 || l2) {
        const n1 = l1 ? l1.val : 0
        const n2 = l2 ? l2.val : 0
        let sum = n1 + n2 + carry
        if (!head) {
            head = tail = new ListNode(sum % 10)
        } else {
            tail.next = new ListNode(sum % 10)
            tail = tail.next
        }
        carry = Math.floor(sum / 10)
        if (l1) {
            l1 = l1.next
        }
        if (l2) {
            l2 = l2.next
        }
    }
    if (carry > 0) {
        tail.next = new ListNode(carry)
    }
    return head
}
```
3. 无重复字符的最长子串  
给定一个字符串 s ，请你找出其中不含有重复字符的 最长子串 的长度。

> 示例 1:  
输入: s = "abcabcbb"  
输出: 3   
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。  

> 示例 2:  
输入: s = "bbbbb"  
输出: 1  
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。  

> 示例 3:  
输入: s = "pwwkew"  
输出: 3  
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。

> 提示：0 <= s.length <= 5 * 104  
s 由英文字母、数字、符号和空格组成
```js
/**
    @param {string} s
    @return {nubmer}
 */

const lengthOfLongestSubstring = (s) => {
    // 哈希集合，记录每一个字符是否出现
    const occ = new Set()
    const n = s.length
    // 右指针，初始值为-1，相当于我们在字符串的左边界的左侧，还没有开始移动
    let rk = -1, ans = 0
    for (let i = 0; i < n; i++) {
        if (i != 0) {
            // 左边界向右移动一格，移除一个字符
            occ.delete(s.charAt(i - 1))
        }
        while(rk + 1 < n && !occ.has(s.charAt(rk + 1))) {
            // 不断移动右指针
            occ.add(s.charAt(rk + 1))
            rk++
        }
        // 第 i 到 rk 个字符是一个极长的无重复字符子串
        ans = Math.max(ans, rk - i + 1)
    }
    return ans
}
```

4. 寻找两个正序数组的中位数  
给定两个大小分别为 m 和 n 的正序（从小到大）数组 nums1 和 nums2。请你找出并返回这两个正序数组的 中位数 。  
算法的时间复杂度应该为 O(log (m+n)) 。  

 

> 示例 1：  
输入：nums1 = [1,3], nums2 = [2]
输出：2.00000
解释：合并数组 = [1,2,3] ，中位数 2

>示例 2：  
输入：nums1 = [1,2], nums2 = [3,4]
输出：2.50000
解释：合并数组 = [1,2,3,4] ，中位数 (2 + 3) / 2 = 2.5

>提示：  
nums1.length == m
nums2.length == n
0 <= m <= 1000
0 <= n <= 1000
1 <= m + n <= 2000
-106 <= nums1[i], nums2[i] <= 106
```js
/**
    @param {number[]} nums1
    @param {number[]} nums2
    @return {number}
*/

const findMedianSortedArrays = (nums1, nums2) => {
    if (nums1.length > nums2.length) {
        let temp = nums1
        nums1 = nums2
        nums2 = temp
    }

    let m = nums1.length
    let n = nums2.length

    // 分割线左侧元素需要满足 m + (n - m + 1) / 2
    let totalLeft = Math.floor((m + n + 1) / 2)

    // 分割线nums1 [0, m] 区间查找
    // 满足 nums1[i - 1] <= nums2[j] && nums2[j - 1] <= nums1[i]

    let left = 0
    let right = m

    while(left < right) {
        let i = Math.floor((left + right + 1) / 2)
        let j = totalLeft - i
        if (nums1[i - 1] > nums2[j]) {
            // 下一个区间搜索 [0, i - 1]
            right = i - 1
        } else {
            left = i
        }
    }

    let i = left
    let j = totalLeft - i

    let nums1LeftMax = i === 0 ? -Infinity : nums1[i - 1]
    let nums1RightMin = i === m ? Infinity : nums1[i]
    let nums2LeftMax = j === 0 ? -Infinity : nums2[j - 1]
    let nums2RightMin = j === n ? Infinity : nums2[j]

    if ((m + n) % 2 === 1) {
        return Math.max(nums1LeftMax, nums2LeftMax)
    } else {
        return (Math.max(nums1LeftMax, nums2LeftMax) + Math.min(nums1RightMin, nums2RightMin)) / 2
    }
}
```