# Arrays

+ [Two Sum](#two-sum)
+ [3Sum](#3sum)
+ [Subarray Sum](#subarray-sum)

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


```python
#first solution
def threeSum(self, nums):
    nums.sort()
    result = []
    for one in range(len(nums)-2):
        if one > 0 and nums[one] == nums[one-1]:
            continue
        two = one + 1
        three = len(nums) - 1
        while two < three:
            sum = nums[one] + nums[two] + nums[three]
            if sum < 0:
                two = two + 1
            elif sum > 0:
                three -= 1
            else:
                result.append([nums[one], nums[two], nums[three]])
                while two < three and nums[two] == nums[two+1]:
                    two += 1
                while three > two and nums[three] == nums[three-1]:
                    three -= 1
                two += 1
                three -= 1
    return result

#second solution
def threeSum(self, nums):
    result = set()
    if len(nums) < 3:
        return result
    if nums.count(0) >= 3:
        result.add((0, 0, 0))
    nums_set = set(nums)
    numMax, numMin = max(nums_set), min(nums_set)
    if numMax <= 0 or numMin >= 0:
        return result
    setA = set(num for num in nums_set if (num > 0 and num <= -2 * numMin))
    setN = set(num for num in nums_set if (num < 0 and num >= -2 * numMax))
    count = collections.Counter(nums)
    for numA in setA:
        for numN in setN:
            num1 = -numA-numN
            if num1 in nums_set:
                val = tuple(sorted([num1, numA, numN]))
                if val.count(num1) <= count[num1] and val.count(numA) <= count[numA] and val.count(numN) <= count[numN]:
                    result.add(val)
    return result

```

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
