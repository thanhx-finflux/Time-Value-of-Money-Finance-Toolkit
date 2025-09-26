# Time-Value-of-Money-Finance-Toolkit
A Python-based toolkit for investment analysis. This project calculates key financial metrics: NPV, IRR, payback period, profitability index, and loan amortization.


## Features
- Net present value (NPV)
- Internal rate of return (IRR)
- Modified IRR (MIRR)
- Payback period
- Profitability index
- Loan amortization schedule
- Case study: **Apple stock vs. Vietnamese Government Bond**
- Visualizations: cash flows & NPV vs. discount rate curve

## Example
```python
import numpy_financial as npf
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Apple Inc. (AAPL), Apple pays a quarterly dividend of $0.26 per share.
# Assuming investors hold the stock for 5 years, and the stock price appreciates to $150 per share.
# Buy 100 shares at $120 each.
# Assuming the discount rate is 8%.
initial_investment = -120 * 100  # Buying 100 shares at $120 each
dividends = [0.26 * 100] * 20  # Quarterly dividends
final_stock_price = 150 * 100  # Selling 100 shares at $150 each
cash_flows = dividends + [final_stock_price]
npv_value = npv(0.08, [initial_investment] + cash_flows)
print(f'Net Present Value (NPV) of Stock Investment: {npv_value:.2f}')
irr_value = irr([initial_investment] + cash_flows)
print(f'Internal Rate of Return (IRR) of Stock Investment: {irr_value:.2%}')

# Vietnamese government bond (VGB) with a face value of $1000, a coupon rate of 6%, and a maturity of 5 years.
# The bond pays semi-annual interest and is purchased at a discount price of $950.
# Assuming the discount rate is 3.75%.
initial_investment = -950  # Buying the bond at a discount price
coupon_payment = 0.06 * 1000 / 2  # Semi-annual coupon payment
cash_flows = [coupon_payment] * 10 + [1000]  # Semi-annual payments for 5 years + face value at maturity
npv_value = npv(0.0375, [initial_investment] + cash_flows)
print(f'Net Present Value (NPV) of Bond Investment: {npv_value:.2f}')
irr_value = irr([initial_investment] + cash_flows)
print(f'Internal Rate of Return (IRR) of Bond Investment: {irr_value:.2%}')

```

    Net Present Value (NPV) of Stock Investment: -8764.89
    Internal Rate of Return (IRR) of Stock Investment: 1.26%
    Net Present Value (NPV) of Bond Investment: -36.61
    Internal Rate of Return (IRR) of Bond Investment: 3.32%

```python
# Loan Amortization
principal = 10000  # Loan amount
annual_rate = 0.05  # Annual interest rate
years = 5  # Loan term in years
amortization_schedule = loan_amortization(principal, annual_rate, years)
print('Loan Amortization Schedule:')
print(amortization_schedule)
```
```
Loan Amortization Schedule:
    Period     Payment   Principal   Interest      Balance
0        1  188.712336  147.045670  41.666667  9852.954330
1        2  188.712336  147.658360  41.053976  9705.295970
2        3  188.712336  148.273603  40.438733  9557.022367
3        4  188.712336  148.891410  39.820927  9408.130957
4        5  188.712336  149.511791  39.200546  9258.619166
5        6  188.712336  150.134757  38.577580  9108.484410
6        7  188.712336  150.760318  37.952018  8957.724092
7        8  188.712336  151.388486  37.323850  8806.335606
8        9  188.712336  152.019271  36.693065  8654.316334
9       10  188.712336  152.652685  36.059651  8501.663649
10      11  188.712336  153.288738  35.423599  8348.374911
11      12  188.712336  153.927441  34.784895  8194.447470
12      13  188.712336  154.568805  34.143531  8039.878665
13      14  188.712336  155.212842  33.499494  7884.665823
14      15  188.712336  155.859562  32.852774  7728.806261
15      16  188.712336  156.508977  32.203359  7572.297284
16      17  188.712336  157.161098  31.551239  7415.136186
17      18  188.712336  157.815936  30.896401  7257.320250
18      19  188.712336  158.473502  30.238834  7098.846748
19      20  188.712336  159.133808  29.578528  6939.712940
20      21  188.712336  159.796866  28.915471  6779.916074
21      22  188.712336  160.462686  28.249650  6619.453388
22      23  188.712336  161.131281  27.581056  6458.322107
23      24  188.712336  161.802661  26.909675  6296.519446
24      25  188.712336  162.476839  26.235498  6134.042607
25      26  188.712336  163.153826  25.558511  5970.888782
26      27  188.712336  163.833633  24.878703  5807.055149
27      28  188.712336  164.516273  24.196063  5642.538875
28      29  188.712336  165.201758  23.510579  5477.337118
29      30  188.712336  165.890098  22.822238  5311.447019
30      31  188.712336  166.581307  22.131029  5144.865712
31      32  188.712336  167.275396  21.436940  4977.590316
32      33  188.712336  167.972377  20.739960  4809.617939
33      34  188.712336  168.672262  20.040075  4640.945677
34      35  188.712336  169.375063  19.337274  4471.570615
35      36  188.712336  170.080792  18.631544  4301.489823
36      37  188.712336  170.789462  17.922874  4130.700360
37      38  188.712336  171.501085  17.211252  3959.199275
38      39  188.712336  172.215673  16.496664  3786.983603
39      40  188.712336  172.933238  15.779098  3614.050364
40      41  188.712336  173.653793  15.058543  3440.396571
41      42  188.712336  174.377351  14.334986  3266.019221
42      43  188.712336  175.103923  13.608413  3090.915297
43      44  188.712336  175.833523  12.878814  2915.081775
44      45  188.712336  176.566162  12.146174  2738.515612
45      46  188.712336  177.301855  11.410482  2561.213758
46      47  188.712336  178.040612  10.671724  2383.173145
47      48  188.712336  178.782448   9.929888  2204.390697
48      49  188.712336  179.527375   9.184961  2024.863322
49      50  188.712336  180.275406   8.436931  1844.587916
50      51  188.712336  181.026553   7.685783  1663.561362
51      52  188.712336  181.780831   6.931506  1481.780532
52      53  188.712336  182.538251   6.174086  1299.242281
53      54  188.712336  183.298827   5.413510  1115.943454
54      55  188.712336  184.062572   4.649764   931.880882
55      56  188.712336  184.829499   3.882837   747.051382
56      57  188.712336  185.599622   3.112714   561.451760
57      58  188.712336  186.372954   2.339382   375.078806
58      59  188.712336  187.149508   1.562828   187.929298
59      60  188.712336  187.929298   0.783039     0.000000
```

## Visualization 

<img width="862" height="545" alt="Image" src="https://github.com/user-attachments/assets/38c10e1c-63a7-4114-8677-d527ca1a7bff" />

<img width="862" height="545" alt="image" src="https://github.com/user-attachments/assets/800583f2-06d7-4410-a397-43b07367474c" />


<img width="862" height="545" alt="Image" src="https://github.com/user-attachments/assets/5eea7e0c-298c-409c-92b0-eb8efd9b8b3f" />


## Technology requirements

    Python 3.8+
    numpy
    numpy_financial
    matplotlib
    Jupyter Notebook

## Contact

  - Name: Thanh Xuyen, Nguyen
  - LinkedIn: https://www.linkedin.com/in/xuyen-thanh-nguyen-0518/
  - Email: thanhxuyen.nguyen@outlook.com


