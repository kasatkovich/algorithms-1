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

```python
def eraseOverlapIntervals(self, intervals):
    if not intervals:
        return 0
    intervals = sorted(intervals, key=lambda x: x[0])
    removed = 0
    _, prev_end = intervals[0]
    for begin, end in intervals[1:]:
        if begin < prev_end:
            removed += 1
            prev_end = min(prev_end, end)
        else:
            prev_end = end
    return removed

```
