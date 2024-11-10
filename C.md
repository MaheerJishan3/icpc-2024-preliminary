# C. Watering the Flowerbed

## Problem Summary

In the magical lands of Numeria, you are responsible for caring for a legendary garden containing N flowerbeds, each filled with delicate flowers that require careful watering.

Each flowerbed has two critical watering requirements:
    
    If the i-th flowerbed is not watered within Xi​ days since its last watering, the flowers will dry out and die.
    If the i-th flowerbed is watered again within Yi​ days since its last watering, the excess water will harm the roots, potentially leading to the plants' death.

All flowerbeds have been watered today, and you need to ensure their health over the next K days.

The challenge is to determine the minimum total number of times you need to water the flowerbeds during this period.

Each watering event on a given day counts separately, even if multiple flowerbeds are watered.

## Solution

### Thought Process

Our approach was to divide the max number of days the flower can survive with the days we have to take care of them.

Let's say we have 2 flowerbeds and we have to take care of them for 10 days.

The first flower was watered today and it needs water in 3 days and I can't water it after 1 day.

The second flower was also watered today and it needs water in 6 days and I can't water it after 3 days.

So I have to water the first flower on day 3, 6 & 9 and water the second flower on day 6 only.

### Code
```python
import math

tests = int(input())

for i in range(tests):
    [flowers, days] = input().split(" ")
    flowers = int(flowers)
    days = int(days)

    result = 0

    for j in range(flowers):
        [max_days, min_days] = input().split(" ")
        min_days = int(min_days)
        max_days = int(max_days)

        result += math.floor(days / max_days)

    print(f"Case {i+1}: {result}")

```
