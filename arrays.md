# Arrays

+[Two Sum](#two-sum)
+[3Sum](#3sum)
+[Subarray Sum](#subarray-sum)

## Two Sum

https://leetcode.com/problems/two-sum/


## 3Sum

https://leetcode.com/problems/3sum/



## Subarray Sum

https://leetcode.com/problems/subarray-sum-equals-k/

```python
def subarraySum(self, nums, k):
        c = 0
        sum = 0
        d = {0: 1}
        for i in range(len(nums)):
            sum = sum + nums[i]
            if sum-k in d.keys():
                c = c + d.get(sum - k)
            d.update({sum: d.setdefault(sum, 0)+1})
        return c

```
