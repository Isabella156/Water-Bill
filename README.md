**University of Leeds School of Computing**

Procedural Programming COMP1711/XJCO1711

Semester 1, 2020-2021

**Coursework 1**

30 marks (20% of the total module mark)

**To be submitted before: 23:59 16/10/2020**

**Late penalties: 5% will be deducted from your overall mark for every late day**

# Skills Tested

This coursework will test your ability to write C code that correctly uses variables, expressions, assignment, and conditional execution (the ‘if’ statement).

# The Brief

You will write a program for a water company. The program can calculate and print water bills for different customers. It can also compute and print a report of the company's financial revenue, profit, and other useful statistics.

# The Details

To encourage customers to save water without penalizing low consumers, a water company has introduced an incremental tariff system. In this system, the price (tariff) of one cubic meter of water increases with increased consumption. To compute water charges, the overall quarterly[^1] consumption of a customer is divided into bands, with consumption at higher bands charged a higher unit price than consumption at lower bands, as shown in the following table:

|              |                                  |                       |
|--------------|----------------------------------|-----------------------|
| **Band No.** | **Water Consumption Range (m³)** | **Unit Price (£/m³)** |
| 1            | 1 – 5                            | 0.20                  |
| 2            | 6 – 12                           | 0.35                  |
| 3            | 13 - 25                          | 0.5                   |
| 4            | 26 - 40                          | 0.75                  |
| 5            | Above 40                         | 2.5                   |

*Examples:*

1\. A customer consumed 3m³ in one quarter.

The total consumption of this customer is in band 1, hence they pay:

water charge = 3 \* 0.2 = £0.6

2\. A customer consumed 14m³ in one quarter.

This customer has reached band 3, hence they pay £0.2 for each of the 5 cubic meters in band 1, £0.35 for each of the 7 cubic meters in band 2, and £0.35 for each of the 2 cubic meters they consumed in band 3:

water charge = 5 \* 0.2 + 7 \* 0.35 + 2 \* 0.5 = £4.45

3\. A customer consumed 41 m³ in one quarter.

water charge=5\*0.2 + (12-5)\*0.35 + (25-12)\*0.5 + (40-25)\*0.75 + (41-40)\*2.5= £23.7

In addition to the cost of fresh water, a customer is also charged for processing waste water that returns to the sewerage system. The company estimates the amount of water that returns to sewer at 95% of the total freshwater consumption. The charge for waste water is £0.25/m³.

Also, customers have to pay a fixed fee of £10 per quarter for processing surface water (e.g. rain water) that drains to the public sewer from their property. Finally, each customer is charged a fixed daily (standing) charge of £0.10 per day.

In addition to domestic customers, the company also serves commercial customers. These customers pay the maximum tariff (of band 5) on all their consumption. Commercial customers also pay waste water charges at £2/m³, a surface water charge of £50 per quarter, and a standing charge of £1.30 per day.

Commercial customers have to pay value added tax (VAT) at a rate of 20% on the total amount of the bill, but domestic customers are exempt from VAT.

For simplicity, assume that there are exactly 91 days in one quarter.

Note: The above rates are hypothetical, so please do not use them to compare prices with your water provider!

# The Task

Write a C program that can be used to:

1\) Compute and print the bill for any customer.

2\) Compute the following quarterly sums and values:

1.  The total amount of fresh water consumed by all customers.

2.  The total amount of fresh water consumed by domestic customers.

3.  The total amount of revenue from all bills (this should not include collected VAT since this must be forwarded to the government).

4.  The total cost of providing water to customers. Assume that one cubic meter of water costs the company an average value of £1. This value covers all costs including fresh and wastewater processing, pumping, maintenance, wages, advertising, …etc.

5.  The profit (or loss!) of the company. Remember that profit = revenue – cost.

6.  The income tax the company has to pay to the government assuming an income tax rate of 30%.

7.  The average value of a domestic bill.

8.  The maximum value of a domestic bill.

The program should be menu driven, i.e. when you run the program a menu similar to this one should appear:

The program waits for the user to enter the number of an option.

If the user enters 1, the program prompts the user to enter the type of this customer (i.e. domestic or commercial). For the type of customer, we use 1 for domestic customers and 2 for commercial customers. The program then prompts the user to enter the amount of quarterly water consumption of this customer. Finally, the program computes the bill and display it on the screen. The bill should include the following details:

- Type of customer (domestic or commercial)

- Amount of fresh water consumption

- Fresh water charges

- Waste water charges

- Surface water charges

- Standing charges

- Amount of VAT

- Total amount to pay

After ‘printing’ the bill, the program should redisplay the menu again and wait for the user to enter a choice.

If the user selects choice number 2, the program displays the quarterly report, then redisplays the menu again.

Finally, to quit the program the user enters 3.

# Implementation Guidelines

- Write the program in standard C. If you write your code in any other language, it will NOT be assessed and you will get a zero mark.

- This is an individual project, and you are not supposed to work with other students.

- I have provided you with a file template – called water.c - for you to complete. Please don’t change the name of this file and use a plain text editor to add your code to the file. I recommend that you use the Atom editor available on our Linux computers.

- I have already implemented the menu code for you. You only need to complete the sections for computing domestic and commercial bills, and for computing the sums mentioned above. The code sections that you have to complete are clearly marked in the file. Other parts of the file – clearly marked as “don’t change” sections– should not be altered in any way as this can cause your code to fail the Autograder tests (see below).

- Also, please do not insert any scanf or printf statements into your code as this will also cause the autograder to fail. If you inserted any scanf or printf statements for debugging purposes, please remove them before submitting you file to Gradescope.

- At the top of the template file, you will find the following header section within comments. Please fill in your name, student id, email, and the date on which you commenced writing the program:

> /\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
>
> University of Leeds
>
> School of Computing
>
> COMP1711/XJCO1711- Procedural Programming
>
> Coursework 1
>
> I confirm that the following code has been developed and written by me and it is entirely the result of my own work. I also confirm that I have not copied any parts of this program from another person or any other source or facilitated someone to copy this program from me.
>
> I confirm that I will not publish the program online or share it with anyone without permission of the module leader.
>
> Student Name:
>
> Student ID:
>
> Email:
>
> Date Work Commenced:
>
> \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/
>
> **If you do not include the above statement in your submitted file, your coursework may be rejected, and you will score 0 in this coursework.**

- **Be aware that plagiarising your code will earn you a zero mark and will have very serious consequences. It is much better to submit your own partially finished work, than to fall into the trap of plagiarism. We use software to detect plagiarism, so if you work with someone else (collusion), or submit someone else’s work (plagiarism), it will be detected.**

# Submission and Grading

- Before submitting your coursework, you must make sure that you can compile your program on our school’s Linux machines. You have already been given instructions on how to access these machines remotely. **If you cannot remotely access our Linux computers, please tell the module leader immediately**. You must also thoroughly test your program on these machines. Submissions that do not compile and run on our Linux machines will score zero even if they work perfectly well on another platform. Hence, if you have developed your program on a Windows or Mac PC, you must not submit your project until you have made sure that it does compile and run on our Linux computers without any problems.

- This assignment will be marked using an automatic grading platform called Gradescope. You can find the link to Gradescope in the ‘Submit My Work’ area on Minerva.

- You should only submit your completed template file - i.e. the ‘water.c’ file - to Gradescope. **Please don’t change the name of this file as this will cause the autograder to fail.**

- Before submitting your code to Gradescope, you should thoroughly test it yourself. You should in particular check bills for domestic consumption values at the boundaries of the bands, such as 0, 1, 5, 6, 12, 13m³…etc. I have also provided you with tables of test data at the end of this document.

- When you submit your file to Gradescope, the autograder will start running immediately and you can see the results of the tests, the marks you have earned, and some feedback about the tests. If your program has failed to pass some of the tests, you can modify your code and re-submit the file again.

# Marking Scheme

The program computes domestic bills correctly (12 marks)

The program computes commercial bills correctly (2 marks)

The program computes the following values correctly:

1.  Total amount of fresh water consumed by all customers. (2 mark)

2.  Total amount of fresh water consumed by domestic customers. (2 mark)

3.  Total amount of revenue from all bills. (2 mark)

4.  Total cost of providing water to customers. (2 mark)

5.  The quarterly profit of the company. (2 mark)

6.  The amount of income tax the company has to pay. (2 mark)

7.  The average of all domestic bills. (2 marks)

8.  The maximum amount of a domestic bill. (2 marks)

# Test Data

Compute the following bills and check the total amount against the table.

|                   |                      |                             |
|-------------------|----------------------|-----------------------------|
| **Customer Type** | **Consumption (m³)** | **Total Amount to Pay (£)** |
| Residential       | 3                    | 20.41                       |
| Residential       | 14                   | 26.88                       |
| Residential       | 0                    | 19.10                       |
| Residential       | 41                   | 52.54                       |
| Commercial        | 60                   | 518.76                      |
| Commercial        | 0                    | 201.96                      |
| Residential       | 1                    | 19.54                       |
| Residential       | 5                    | 21.29                       |
| Residential       | 6                    | 21.88                       |
| Residential       | 13                   | 26.14                       |
| Residential       | 40                   | 49.80                       |
| Commercial        | 17                   | 291.72                      |
| Residential       | 25                   | 34.99                       |
| Residential       | 13                   | 26.14                       |
| Residential       | 30                   | 39.92                       |
| Commercial        | 1                    | 207.24                      |
| Commercial        | 101                  | 735.24                      |
| Residential       | 12                   | 25.40                       |
| Residential       | 13                   | 26.14                       |
| Commercial        | 12                   | 265.32                      |
| Residential       | 77                   | 151.09                      |
| Residential       | 26                   | 35.98                       |

Once you have computed all the above bills, display the sums and statistics and compare your values to the following table:

|                                             |             |
|---------------------------------------------|-------------|
| Sum                                         | Value       |
| Total Fresh Water Consumption               | 510 m³      |
| Total Fresh Water Consumption (Residential) | 319 m³      |
| Total Revenue                               | 2447.41 GBP |
| Total Cost                                  | 510.00 GBP  |
| Profit                                      | 1937.41 GBP |
| Income tax                                  | 484.35 GBP  |
| Maximum Domestic Bill                       | 151.09 GBP  |
| Average Domestic Bill                       | 37.33 GBP   |

END

[^1]: The quarterly water consumption is the water consumption during one quarter. A quarter is a three-month period (i.e. a quarter of a year).
