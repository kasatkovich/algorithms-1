# Arrays

+[Two Sum](#two-sum)
+[3Sum](#3sum)
+[Subarray Sum](#subarray-sum)

## Two Sum

https://leetcode.com/problems/two-sum/

```python
def twoSum(self, nums, target):
    i = 0
    j = len(nums) - 1
    num1 = sorted([(index, elem) for index, elem in enumerate(nums)], key=lambda x: x[1])
    while i != j:
        res = num1[i][1] + num1[j][1]
        if res == target:
            return num1[i][0], num1[j][0]
        elif res > target:
            j -= 1
        else:
            i += 1
    return None    

```

## 3Sum

https://leetcode.com/problems/3sum/



## Subarray Sum

https://leetcode.com/problems/subarray-sum-equals-k/

```python
def subarraySum(self, nums: List[int], k: int) -> int:
    result = 0
    sum = 0
    d = {0: 1}
    for i, item in enumerate(nums):
        sum = sum + item
        if sum - k in d.keys():
            result = result + d.get(sum - k)
        d[sum] = d.setdefault(sum, 0) + 1
    return result

```
