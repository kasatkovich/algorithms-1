# Arrays

+[Two Sum](#two-sum)
+[3Sum](#3sum)
+[Subarray Sum](#subarray-sum)

## Two Sum

https://leetcode.com/problems/two-sum/


## 3Sum

https://leetcode.com/problems/3sum/

def threeSum(self, nums):
        outresult = []
        ourresult = []
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                if(-nums[i]-nums[j] in nums[j+1:len(nums)] and not set([nums[i],nums[j],-nums[i]-nums[j]]) in ourresult):
                    ourresult.append({nums[i],nums[j],-(nums[i]+nums[j])})
                    outresult.append([nums[i],nums[j],-(nums[i]+nums[j])])
        return outresult  

## Subarray Sum

https://leetcode.com/problems/subarray-sum-equals-k/
