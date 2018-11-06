---
title: 'Convert Celsius to Fahrenheit'
date: 2017-07-07 00:00:00
featured_image: '/images/convert_temp.jpg'
---
This program converts temperature to Celsius, using the formula
<img src="https://www.pharmacy-tech-test.com/images/f_c_conv.jpg"/>


```python
# Intialize variables to be used in the program
tempF = 0

# Prompt use for temperature in Celsius
tempC = input("Enter temperature in Celsius. ")

# Convert input to float, because the input system accepts user input as string by default.
# Wrap this within a try-except code block to exit, as the conversion to float will fail if
# the user supplied a non-numeric input!
try:
    tempC = float(tempC)
except ValueError:
    print("Temperature must be an integer.  Please try again.  Goodbye.")

# Use formula to convert temperature from Celsius to Fahrenheit
tempF = (tempC * (9/5))+32

# Print the result
print("The temperature in Fahrenheit is " +str(tempF))
```
