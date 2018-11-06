---
title: 'Find Total, Count, and Average'
date: 2017-07-12 00:00:00
featured_image: '/images/find_total_count_average.jpg'
---

This program will repeatedly read numbers until user types <b>done</b>.  Then program will display total, count, and average of all the numbers. If the user enters something that isn't a number, there will be an error.



```python
# Initialize variables
numList = list()

print('This program will give the total, count, and average of numbers entered')
print('Type done after last number')

while True:
    inp = input('Enter a number:\n')
    if inp == 'done':
        break #program ends when user types done
    try: #error code for non-numeric entry
        inpFloat = float(inp)
        numList.append(inpFloat)
    except:
        print("Input must be numeric")

print('Done!')

# Compute sum, count, and average
numListSum = sum(numList)
numListCount = len(numList)
if numListCount == 0:  # Makes average equal to zero if no numbers were entered
    numListAverage = 0
else:
    numListAverage = numListSum/numListCount



# Display results
print("The total of the numbers entered is "+str(numListSum))
print("The count of numbers entered is " +str(numListCount))
print("The average of numbers entered is " +str(numListAverage))

```
