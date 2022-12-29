---
title:  "Python Calculator"
mathjax: true
layout: post
categories: media
excerpt_separator: <!--more-->
---

![Python calc]({{site.baseurl}}/assets/Images/Python_calc.jpg) 

This is a short code that was made as part of a course. This is the creation of a calculator using Python. This shows the skills on building using 'if/else' statements. 
<!--more-->

```
import math

while True:
    print("\nChoose the math operation.\n\n0 - Addition\n1 - Subtraction\n2 - Multiplication\n3 - Division\n4 - Modulo\n5 - Exponential\n6 - Square root\n7 - Logarithm\n8 - Sine\n9 - Cosine\n10 - Tangent\n")
    oper = input("\nYour option from the menu: ")
#Addition
    if oper == "0":
        val1 = float(input("\nFirst value: "))
        val2 = float(input("\nSecond value: "))
        print("\nResult: " + str(val1 + val2)+ "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break
#Subtraction
    elif oper == "1":
        val1 = float(input("\nFirst value: "))
        val2 = float(input("\nSecond value: "))
        print("\nResult: " + str(val1 - val2)+ "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break 
#Multiplication
    elif oper == "2":
        val1 = float(input("\nFirst value: "))
        val2 = float(input("\nSecond value: "))
        print("\nResult: " + str(val1 * val2)+ "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break 
#Division
    elif oper == "3":
        val1 = float(input("\nFirst value: "))
        val2 = float(input("\nSecond value: "))
        print("\nResult: " + str(val1 / val2)+ "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break 
#Modulo
    elif oper == "4":
        val1 = float(input("\nFirst value: "))
        val2 = float(input("\nSecond value: "))
        print("\nResult: " + str(val1 % val2)+ "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break
#Exponential
    elif oper == "5":
        val1 = float(input("\nEnter the base: "))
        val2 = float(input("\nEnter the power: "))
        print("\nResult: " + str(math.pow(val1, val2))+ "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break
#Square root
    elif oper =="6":
        val1 = float(input("\nEnter the value for extracting the square root: "))

        print("\nResult: " + str(math.sqrt(val1)) + "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break
#Logarithm
    elif oper =="7":
        val1 = float(input("\n Enter the value for calculating the logarithm to base: "))

        print("\nResult: " + str(math.log(val1, 2)) + "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break
#Sine
    elif oper =="8":
        val1 = float(input("\n Enter the value (in degrees) for calculating the sine: "))

        print("\nResult: " + str(math.sin(math.radians(val1))) + "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break
#Cosine
    elif oper =="9":
        val1 = float(input("\n Enter the value (in degrees) for calculating the cosine: "))

        print("\nResult: " + str(math.cos(math.radians(val1))) + "\n")
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break
#Tangent
    elif oper =="10":
        val1 = float(input("\n Enter the value (in degrees) for calculating the tangent: "))

        print("\nResult: " + str(math.tan(math.radians(val1))) + "\n")
#Return to Main Menu
        back = input('\nBack to main menu? (yah / nah)')

        if back == 'yah':
            continue
        else:
            break

#Handling invalid options
    else:
        print("\nInvalid option! Try again.\n")
        continue

#end of code
```