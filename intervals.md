# Intervals

+[Insert Interval](#insert-interval)
+[Merge Intervals](#merge-intervals)
+[Non-overlapping Intervals](#non-overlapping-intervals)

## Insert Interval

https://leetcode.com/problems/insert-interval/


## Merge Intervals

https://leetcode.com/problems/merge-intervals/



## Non-overlapping Intervals

https://leetcode.com/problems/non-overlapping-intervals/

def eraseOverlapIntervals(self, intervals):
        if (intervals == []):
            return 0
        sorted_intervals = sorted(intervals, key = lambda x: x[0])
        end = (sorted_intervals[0])[1]
        min = 0
        for i in range(1,len(sorted_intervals)):
            if((sorted_intervals[i])[0] < end):
                if((sorted_intervals[i])[1] < end):
                    end = sorted_intervals[i][1]
                min = min + 1 
            else:
                end = sorted_intervals[i][1]
        return min        
