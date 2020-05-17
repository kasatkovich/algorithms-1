# Arrays

+[Two Sum](#two-sum)
+[3Sum](#3sum)
+[Subarray Sum](#subarray-sum)

## Two Sum

https://leetcode.com/problems/two-sum/


## 3Sum

https://leetcode.com/problems/3sum/


    def threeSum(self, nums):
        new = set() 
        if len(nums) < 3: return new 
        if nums.count(0) >= 3: new.add((0,0,0)) 
        nums_set = set(nums)
        numMax, numMin = max(nums_set), min(nums_set)
        if numMax <= 0 or numMin >= 0: return new
        setA = set(num for num in nums_set if (num > 0 and num <= -2 * numMin))
        setN = set(num for num in nums_set if (num < 0 and num >= -2 * numMax)) 
        count = collections.Counter(nums)
        for numA in setA:
            for numN in setN:
                num1=-numA-numN
                if num1 in nums_set:
                    val=tuple(sorted([num1,numA,numN]))
                    if val.count(num1)<=count[num1] and val.count(numA)<=count[numA] and val.count(numN)<=count[numN]:
                        new.add(val)
        return new
        
## Subarray Sum

https://leetcode.com/problems/subarray-sum-equals-k/
