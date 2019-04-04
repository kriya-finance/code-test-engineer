# MarketInvoice Coding Exercise

## Loan Repayment Calculator

For loan customers we want to inform them how much a weekly installment will be, the total amount of interest paid and the overall cost of the loan.
For accounting purposes we need to know how much of each repayment is paying off interest and how much is paying off the principal.

## Task

Implement the following user stories:

1. As a prospective loan customer, I want to know the weekly instalment, the total cost and the amount of interest paid for a loan of a given amount and APR.
2. As a loans administrator, I want to know what the breakdown of repayments are in terms of interest paid and principal repaid for a given loan amount and APR.

The system should be Web API with two endpoints returning json.

e.g.

```/loansummary?amount=50000&apr=19```  

will return  
```json
{
  "weeklyRepayment" : 1058,
  "totalRepaid" : 55016,
  "totalInterest" : 5016
}
```
and  

```
/repaymentSchedule?amount=50000&apr=10
```
will return

```json
{
   "installments":[
     {
       "installmentNumber": 1,
       "amountDue": 50000,
       "principal": 875,
       "interest": 183
     },
     
     ...
     
     {
      "installmentNumber": 52,
      "amountDue": 1054,
      "principal": 1054,
      "interest": 4
     }
   ]
}
```

### Examples
 
#### Scenario 1

Given a loan of £50,000 taken out over 52 weeks at an annual interest rate of 19%  
When I ask for the loan summary  
Then I am told
 - the weekly repayment is £1,058
 - the total amount repaid is £55,016 
 - the total interest paid is £5,016.

#### Scenario 2

Given a loan of £50,000 taken out over 52 weeks at an annual interest rate of 19% (assuming the installments are paid back regularly and on time)  
When I ask for the repayment breakdown  
Then I am given a breakdown that includes the following values:

|Repayment Week | Amount Due | Principal | Interest |
|:---:|:---:|:---:|:---:|
| 1 | 50,000 |875 | 183 |
| 2 | 49,125.17|878|179|
| 10 | 42,010.44 |904 | 153 |  
| 26 | 26,184.45 |958 | 99 |
|52| 1,053.68 | 1,054 | 4 |  

(Note: Although we only provide a few examples here, we expect the endpoint to return data for all 52 installments)


### Note

Each installment is calculated using the following formula:

![formula for loans](/Loans_formula.png?raw=true "Loans Formula")

Where
 - P is the amount of the loan (the Principal)
 - n is the number of payments over the life of the loan
 - r is the installment period interest rate (the Annual Percentage Rate divided by the number of installments)
 
https://www.wikihow.com/Calculate-an-Installment-Loan-Payment

### What we pay attention to when we evaluate your submission
* Code quality and consistency
* Readability and simplicity
* Backwards compatibility
* Test quality
* Commit history

## Submission Guidelines
Here are guidelines on how to submit the exercise

### If you are in contact with our Talent Team
* ZIP your code directory, *without* uncommitted / ignored files _(i.e. NuGet packages)_
  - include git, but exclude anything not checked in _(git clean -fdx)_.
* Email the submission in a zip file to our Talent team contact

### Getting in contact with our talent team
Get in touch with us via email at [recruitment@marketinvoice.com](recruitment@marketinvoice.com)!

#### Thank you for taking your time
[MarketInvoice Tech Team](https://github.com/marketinvoice)
