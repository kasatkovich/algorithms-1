# Intervals

+[Insert Interval](#insert-interval)
+[Merge Intervals](#merge-intervals)
+[Non-overlapping Intervals](#non-overlapping-intervals)

## Insert Interval

https://leetcode.com/problems/insert-interval/


## Merge Intervals

https://leetcode.com/problems/merge-intervals/


```python
def merge(self, intervals):
    if not intervals:
        return intervals
    intervals.sort(key=lambda x: x[0])
    new_intervals = []
    check_intervals = intervals[0]
    for interv in intervals[1:]:
        if check_intervals[1] >= interv[0]:
            check_intervals[1] = max(check_intervals[1], interv[1])
        else:
            new_intervals.append(check_intervals)
            check_intervals = interv
    new_intervals.append(check_intervals)
    return new_intervals
  
  ```

## Non-overlapping Intervals

https://leetcode.com/problems/non-overlapping-intervals/

