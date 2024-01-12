# Discount Split Bills

This app was inspired by how my friends split the bill whenever we order food online together.

Let $P_{i}$ represent the regular price of item $i$, $T_{n}$ represent the total sum of all regular prices, and $T_{d}$ represent the price total amount after discounts. In general, the steps are as follows:

1. Begin by adding up all the regular prices of the items on the bill.

   $$T=\sum_{i}P_{i}$$

2. Calculate the percentage each item contributes to the total sum by dividing its individual price by the overall sum.

   $$\text{Percentage of item }i = \frac{P_{i}}{T_{n}}$$

3. Once you have the percentage for each item, apply these percentages to the total bill amount after any discounts have been applied. This will determine the specific value each item holds in the discounted total.

   $$\text{Value of item } i=\text{Percentage of item } i×T_{d}$$
