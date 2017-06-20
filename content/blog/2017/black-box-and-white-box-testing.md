title=Sensitive Data Exposer: Black Box and White Box Test Cases 
date=2017-02-26
type=post
tags=blog
status=published
~~~~~~

**Note:** ATM Use Cases diagram can be viewed on the following link [ATM Example Use Case](http://www.math-cs.gordon.edu/courses/cs211/ATMExample/UseCases.html "ATM Use Cases")

The ATM is designed in a way that once a user has successfully inserted a valid bank card and enters a valid four-digit pin, they are presented with four transaction options: withdrawal, deposit, transfer, and account inquiry. While the user navigates the ATM system, one threat that could pose as a danger to personal identifiable information (PII) is sensitive data exposer. This article is going to focus on the transaction feature/function of the ATM design because this is where the vulnerability is likely to occur.

#### Is threat mitigated by the current design?

It is difficult to determine whether the current design of ATM system mitigates sensitive data exposure because it does not explicitly outline how it addresses or if it recognizes the threat. The assumption will be that the current design does not recognize the sensitive data exposure as a threat. Before we come to a conclusion, we will conduct a black box test to understand how the design reacts to various tests. A high-level design of the ATM system will be used as the basis for tests. The high-level design recognized the threat sensitive data exposure had on PII and took steps to mitigate the vulnerability. These steps included limiting the amount of information displayed on the screen and using generic messages when a transaction is not successful.

### User withdrawals

Each time a user wants to withdrawal N amount, the bank system internally determines whether they can or cannot withdrawal N amount by checking bank account records of the user. A message output depends on whether the user can or cannot withdrawal. If the user can withdrawal N amount, they are prompted to confirm that N amount is to be withdrawn. On the other hand, if the user does not have sufficient funds and cannot withdrawal, they are notified that no withdrawal can be made at that time.

### User inquiring

When a user requests an inquiry to their account, the bank internally checks the user’s account summary of checking account and savings account.  The user is then provided the option of printing out summary on a receipt.

### User transferring

Each time a user wants to transfer N amount, internally the bank system determines whether they can or cannot transfer N amount by checking bank account records of the user. A message output depends on whether the user can or cannot transfer. If the user can transfer N amount, they are prompted to confirm that N amount is to be transferred. On the other hand, if the user does not have sufficient funds in the given account, they are notified that transfer cannot be made at that time.

### User depositing

Once the user indicates that they want to deposit N amount in account, the ATM system prompts the user to specify which account they want to deposit the amount. The user cannot deposit more than $25,000 in either account. The bank internally updates its records once it has determined that indeed the amount deposited is correct.

## Test steps

1. Total amount in checking account.
2. Total amount in saving account.
3. Transfer N amount from checking account to saving account.
4. Transfer N amount from saving account to checking account.
5. Deposit N amount in checking account.
6. Deposit N amount in savings account.
7. Withdrawal N > $1,000 from checking account.
8. Withdrawal N < $10 from savings account.

### Test tools that to perform testing

The tools that I would employ to test sensitive data exposure vulnerability on ATM system would be Katalon Studio and Hp Fortify on Demand. Katalon Studio has the capability of conducting automated tests as well as manual test with the UI layer of an application.

Hp Fortify on Demand provides security as a service and manages security risk. Fortify on demand also has the capabilities of conducting automated tests with a full audit of results. Fortify differs from Katalon Studio because it focuses more on security as a posed to the overall functionality of an application (Fortify on Demand, 2017).


 
