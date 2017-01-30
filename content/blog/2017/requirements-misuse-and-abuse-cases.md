title=Requirements Misuse and Abuse Cases
date=2017-01-29
type=post
tags=blog
status=published
~~~~~~

We attempt to explain briefly what misuse/abuse cases are and why applying the concept in the development stage of software requirements results in a more robust secure product. Programmers generally create use case diagrams to demonstrate functions, flow and actions that the end-user and the application will perform, this ensures the program functions as it should and meets all the desired requirements. Misuse or abuse cases are similar to use cases, only that with misuse/abuse cases the developer has to place themselves in the shoes of an attacker. The programmer walks through functions, flow and actions of the program with the lenses of an attacker – how will the application or user handle the application in a way that is not intended. Misuse cases provide opportunities to investigate and validate security requirements. 

### ATM abuse/misuse cases

![Atm System](/img/re-atm-system.png)

**Note:** The ATM System use cases diagram is displayed above. Use cases diagrams can also be viewed on the following links: 

[ATM Example Use Case](http://www.math-cs.gordon.edu/courses/cs211/ATMExample/UseCases.html "ATM Use Cases")

[ATM Operator Startup Use Case](http://www.math-cs.gordon.edu/courses/cs211/ATMExample/Interactions.html#Startup "Startup Use Case")

#### Start-up Use Case

Before bank customers can begin using the ATM machine, an ATM system operator first has to Start Up the system following this sequence:

    1.	Switch on operator panel
    2.	Get initial cash in the ATM 
    3.	Set initial cash into cash dispenser 
    4.	Then open connection to the bank
 
#### Start-up Misuse/Abuse Case

The first sequence, operator panel being switched on, does not appear to have contingencies in place that authenticates the operator. As a result, what will most likely happen is **broken authentication** and **session management** allowing a malicious user to compromise the entire system placing customer’s personal identifiable information (PII) in danger. To mitigate this threat, operator panel has to prompt user to enter username and password for user authentication. To mitigate **brute force authentication**, **guess valid user accounts** and **dictionary attacks**, a generic error message is shown when authentication fails as well as locking the system after N failed login attempts. 

Lastly, at the moment once the operator set initial cash into cash dispenser a connection to the bank is established. A vulnerability that can occur is **missing function level access control**. This is when a request is not verified, enabling an attacker to forge requests in order to access functionality without proper authorization. To mitigate this vulnerability, operator should be required to enter pin before a connection is established with bank.

#### Session Use Case

After start-up sequence is successful customers are free to begin sessions. Sessions should follow the following sequence:

    1.	Valid bank card inserted into ATM
    2.	Session is created. Reading card. If card is valid request to enter pin, if card is not valid terminate session.
    3.	User enters valid pin 
    4.  If pin valid, user can perform following transactions
            a. Withdrawal
            b. Deposit
            c. Transfer
            d. Inquiry
    5.	User cancels session (this can be done at any stage of session)
    6.  Card ejected

#### Session Misuse/Abuse Case

Once the ATM has detected the inserted bank card is valid, the customer is prompted to enter a four-digit pin. This user authentication is threatened by **brute force authentication** and **dictionary attacks**.  To mitigate these threats, the ATM should lock account after N failed login attempts as well as validate the minimum length and complexity of pin. It is important that when user enters wrong pin a generic error message is shown to ensure that an attacker is not provided clues as to which user account is stored in the bank. All these implemented measures collectively in return mitigate **broken authentication** and **session management**.

#### Transaction Use Case

After a successful pin validation, customer is presented with four transaction options: withdrawal, deposit, transfer, and inquiry. 

#### Transaction Misuse/Abuse Case

In order to mitigate the threat of **sensitive data exposer**, it is critical that the ATM displays the minimum number of information for each transaction. To give an example, let’s say a customer wants to withdrawal N amount from checking account. If N amount is more than amount in checking account, the ATM system should display a generic message ensuring PII is protected. To take it further, for each transaction, whether it is withdrawal, deposit, transfer, or inquiry, the customer needs to be prompted with a message asking for a confirmation to carry out an action. This will ensure that **missing function level access control** is mitigated to some extent.

**Sources:**

OWASP Top Ten Project. Top 10 2013-Top 10. 2002-2013 OWASP Foundation. Retrieved from https://www.owasp.org/index.php/Top_10_2013-Top_10




