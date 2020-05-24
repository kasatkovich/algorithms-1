# Intervals

+[Insert Interval](#insert-interval)
+[Merge Intervals](#merge-intervals)
+[Non-overlapping Intervals](#non-overlapping-intervals)

## Insert Interval

https://leetcode.com/problems/insert-interval/


```python
def insert(self, intervals, newInterval):
    if not newInterval:
        return intervals
    intervals.append(newInterval)
    if not intervals:
        return intervals
    intervals.sort(key=lambda x: x[0])
    new_intervals = []
    check_intervals = intervals[0]
    for i, item in enumerate(intervals):
        if check_intervals[1] >= (intervals[i])[0]:
            check_intervals[1] = max(check_intervals[1], (intervals[i])[1])
        else:
            new_intervals.append(check_intervals)
            check_intervals = intervals[i]
    new_intervals.append(check_intervals)
    return new_intervals

```

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
