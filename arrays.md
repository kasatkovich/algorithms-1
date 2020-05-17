# Arrays

+[Two Sum](#two-sum)
+[3Sum](#3sum)
+[Subarray Sum](#subarray-sum)

## Two Sum

https://leetcode.com/problems/two-sum/

   def twoSum(self, nums, target):
        seen = {}
        for i, v in enumerate(nums):
            complement = target - v
            if (complement in seen):
                return [seen[complement],i]
            seen[v]= i

## 3Sum

https://leetcode.com/problems/3sum/



## Subarray Sum

https://leetcode.com/problems/subarray-sum-equals-k/
