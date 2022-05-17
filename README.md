The Project Goals
Short term: Construct prepayment prediction models
Longer-term:
Generate long term projection on prepayment for the mortgage 
Improve the accuracy of our prediction models 
Create a pipeline building enabling automated processing and benchmark comparison with Nomura’s model results. Our end goal is to produce a model that takes value input and come up with forecasted Prepayment Probability

Background Introduction
A mortgage-backed security (MBS) is an investment similar to a bond that is made up of a bundle of home loans bought from the banks that issued them. Investors in MBS receive periodic payments similar to bond coupon payments.

Mortgage borrowers are able to choose to repay part of the principal before the maturity date. There is the prepayment option for the rational borrowers, and prepayments make the mortgage payment process more complex and add more uncertainty. The aim of our prepayment model is to explain the relationship between prepayment indicator and a group of chosen explanatory variables using data mining techniques, and finally build a pipeline that allows the user to enter specific CUSIP and outputs the prepayment probability. 

Data Description
We obtain our data sets directly from Fannie Mae and Freddie Mac websites. Amongst the huge pool of available Mortgage Backed Securities data sets, we are basing our analysis off of Single-Class/ Single-Class Resecuritization Monthly Loan Level data. And the time period for our analysis would be the prior six months since the start of our analysis, which are from August 2021 to February 2022.

We are considering merging external data sources to further our analysis and provide more realistic projections on our targets. Some thoughts and potential items we want to include are interest rate, CPI, FICO score, etc.

We may also feed in the most current data sets from our primary source as new monthly outcome releases.

Progress
Data Cleaning

Data cleaning is an important part of our project, since the data file is so huge. We are required to deal with 6 month’s data respectively from Fannie Mae and Freddie Mac, and each data set contains 150 thousand rows. We clean the data in the following steps:

Drop columns with mostly null values
Filter the data to where the original interest rate equals current interest rate
Filter the data to single family

While we did the data cleaning, the data set is still so big that our computers are not capable of handling such a large amount of data. We tried to take out sample sets to build models and make calculations. However, it will result in some inaccuracy in our calculation. Currently we are thinking of chunking it or building a SQL database.

CPR Calculation

CPR is the constant prepayment rate and it can be treated as the prepayment speed of a mortgage loan pool. CPR is often used to measure the prepayment risk, and it is the target variable of our model. We calculate it in the following way: 

Monthly principal payment = Monthly payment – Monthly interest
Monthly payment  = P [ I ( 1 + I )^N ] / [ ( 1 + I )^N – 1 ] where
i.    P = Principal amount (Mortgage loan amount)
ii.    I = Interest rate on the mortgage (Current Net Interest Rate / 1200)
iii.    N = Number of periods (Loan term)
iv.    calculate monthly payment and monthly interest at loan level before aggregating to CUSIP level
Scheduled Principal Balance = Current Investor Loan – monthly principal payment

Characteristics Analysis
Currently we are making a summary of different characteristics and performing data visualizations to analyze the relationship between prepayment and different characteristics. This step will help us with a better understanding of how to build predictive models in the future.

There are many reasons why borrowers decide to make prepayments on their mortgage loan. The factors might be related to borrowers' personal characteristics such as age, income, credit score, loan characteristics such as loan age, interest rate, prepayment penalty, and property type, and macroeconomic data such as month of the year, housing prices. Because there are numerous variables which are related to clients’ specifics, mortgage characteristics or macroeconomic factors, we made an analysis of variable characteristics through data visualization and understanding, and then found the relationship between these variables and prepayment rate. 

The key characteristics we are analyzing are shown below:
Credit score
Geographic locations
Year/quarter/month
Average unpaid principal balance of a loan (UPB)
Loan Age
Mortgage type
Loan Term 
Property type 
Loan purpose 
Subprime loan rate 
Prepayment Penalty
DTI (Debt to Income Ratio)

