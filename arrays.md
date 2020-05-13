# Arrays

+[Two Sum](#two-sum)
+[3Sum](#3sum)
+[Subarray Sum](#subarray-sum)

## Two Sum

https://leetcode.com/problems/two-sum/

def twoSum(self, nums, target):
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                if (nums[i]+nums[j] == target):
                    return [i,j]

## 3Sum

https://leetcode.com/problems/3sum/



## Subarray Sum

https://leetcode.com/problems/subarray-sum-equals-k/
