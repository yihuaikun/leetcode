# [325. 和等于 k 的最长子数组长度](https://leetcode-cn.com/problems/maximum-size-subarray-sum-equals-k)

[English Version](/solution/0300-0399/0325.Maximum%20Size%20Subarray%20Sum%20Equals%20k/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给定一个数组 <em>nums</em> 和一个目标值 <em>k</em>，找到和等于<em> k </em>的最长子数组长度。如果不存在任意一个符合要求的子数组，则返回 0。</p>

<p><strong>注意:</strong><br>
&nbsp;<em>nums</em> 数组的总和是一定在 32 位有符号整数范围之内的。</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入: </strong><em>nums</em> = <code>[1, -1, 5, -2, 3]</code>, <em>k</em> = <code>3</code>
<strong>输出: </strong>4 
<strong>解释: </strong>子数组 <code>[1, -1, 5, -2]</code> 和等于 3，且长度最长。
</pre>

<p><strong>示例 2:</strong></p>

<pre><strong>输入: </strong><em>nums</em> = <code>[-2, -1, 2, 1]</code>, <em>k</em> = <code>1</code>
<strong>输出: </strong>2 <strong>
解释: </strong>子数组<code> [-1, 2]</code> 和等于 1，且长度最长。</pre>

<p><strong>进阶:</strong><br>
你能使时间复杂度在 O(<em>n</em>) 内完成此题吗?</p>

## 解法

<!-- 这里可写通用的实现逻辑 -->

哈希表 + 前缀和。

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class Solution:
    def maxSubArrayLen(self, nums: List[int], k: int) -> int:
        mp = {0: -1}
        s = ans = 0
        for i, v in enumerate(nums):
            s += v
            if s - k in mp:
                ans = max(ans, i - mp[s - k])
            if s not in mp:
                mp[s] = i
        return ans
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class Solution {
    public int maxSubArrayLen(int[] nums, int k) {
        Map<Integer, Integer> mp = new HashMap<>();
        mp.put(0, -1);
        int s = 0;
        int ans = 0;
        for (int i = 0; i < nums.length; ++i) {
            s += nums[i];
            if (mp.containsKey(s - k)) {
                ans = Math.max(ans, i - mp.get(s - k));
            }
            if (!mp.containsKey(s)) {
                mp.put(s, i);
            }
        }
        return ans;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    int maxSubArrayLen(vector<int>& nums, int k) {
        unordered_map<int, int> mp;
        mp[0] = -1;
        int s = 0, ans = 0;
        for (int i = 0; i < nums.size(); ++i)
        {
            s += nums[i];
            if (mp.count(s - k)) ans = max(ans, i - mp[s - k]);
            if (!mp.count(s)) mp[s] = i;
        }
        return ans;
    }
};
```

### **Go**

```go
func maxSubArrayLen(nums []int, k int) int {
	mp := map[int]int{0: -1}
	s, ans := 0, 0
	for i, v := range nums {
		s += v
		if j, ok := mp[s-k]; ok {
			ans = max(ans, i-j)
		}
		if _, ok := mp[s]; !ok {
			mp[s] = i
		}
	}
	return ans
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### **...**

```

```

<!-- tabs:end -->
