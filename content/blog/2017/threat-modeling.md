title=Threat Modeling 
date=2017-02-12
type=post
tags=blog
status=published
~~~~~~

Building on the previous article where we discussed [misuse/abuse case](https://makumbi.github.io/output/blog/2017/requirements-misuse-and-abuse-cases.html "misuse/abuse cases") using ATM machine as an example, this week we discuss the threat modeling process. Threat modeling ranks threats during software design identifying which assets or components are most critical to the business and ranks them according to damage a threat would cause to the business. This ranking helps teams prioritize energy and resources on high ranking assets during a breach in an effort to mitigate damage. As a result, security code review of components whose threat modeling has ranked with high risk threat is prioritized.

Threat modeling process encompasses three high level steps which are decompose the application, determine and rank threats, and determine countermeasures and mitigation. We are going to delve deep into each step to get a better understanding how threat modeling is implemented.

**Decompose the Application**
>> As the first step in threat modeling process, attention is focused on gaining an understanding of the application and how it interacts with external entities. What does this mean? It means identifying entry points an attacker can use to exploit the application, identify trust levels as it pertains to access levels among others.

**Determine and rank threats**
>> It is not hard to guess what this step is all about. Threats are determined and ranked using a threat categorization methodology. OWASP outlines a threat categorization known as STRIDE, which we will be using to rank threats to the ATM machine. STRIDE stands for – Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, and Elevation of privilege.

**Determine countermeasures and mitigation**
>> Once a risk ranking is assigned to the threats, it is possible to sort threats from the highest to the lowest risk, and prioritize the mitigation effort, such as by responding to such threats by applying the identified countermeasures.

#### External Dependences

We also outline external dependences. External dependences are items external to the code of the application that may pose a threat to the application (OWASP, 2015). For our ATM machine, an external dependency would be the machine’s connection to the bank both internally and physically.

#### Entry Points

Entry points are essentially an application’s attack surface. Meaning that we define the interfaces which potential attackers can interact with the application or supply it with data. For our ATM machine, the entry points are the pin pad, credit card reader, bank and operator.

#### Assets

Threat models are created during the design of an application to outline threat targets. Threat targets are things that attackers are interested in, this can be items/areas of interest. Assets are the reason threats will exists. Assets can be both physical and abstract. For our ATM machine, an abstract asset might be degrading people’s trust in using ATM machines. A physical asset might be a list of account records and personal information, as well as the actual stealing of money.

#### Ranking of Threats

Threats are ranked according to potential risk factors. Risk factors are determined by the impact they pose to a business and component and ranked in a list of high, medium, low risk. DREAD is a Microsoft threat-risk ranking model that we will use to rank threat factors. The risk factorization of the model allows the use of values influencing factors of a threat. Questions that threat-risk ranking model aims to answer are:
- For Damage: How big would the damage be if the attack succeeded?
- For Reproducibility: How easy is it to reproduce an attack to work?
- For Exploitability: How much time, effort, and expertise is needed to exploit the threat?
- For Affected Users: If a threat were exploited, what percentage of users would be affected?
- For Discoverability: How easy is it for an attacker to discover this threat?

### Mitigation for threats.

Once the ATM has detected the inserted bank card is valid, the customer is prompted to enter a four-digit pin. This user authentication is threatened by **brute force authentication** and **dictionary attacks**.  To mitigate these threats, the ATM should lock account after N failed login attempts as well as validate the minimum length and complexity of pin. It is important that when user enters wrong pin a generic error message is shown to ensure that an attacker is not provided clues as to which user account is stored in the bank. All these implemented measures collectively in return mitigate **broken authentication** and **session management**.

In order to mitigate the threat of **sensitive data exposure**, it is critical that the ATM displays the minimum number of information for each transaction. To give an example, let’s say a customer wants to withdrawal N amount from checking account. If N amount is more than amount in checking account, the ATM system should display a generic message ensuring PII is protected. To take it further, for each transaction, whether it is withdrawal, deposit, transfer, or inquiry, the customer needs to be prompted with a message asking for a confirmation to carry out an action.

**Sources**

Bjork C. Russell. ATM Simulation. Retrieved from http://www.math-cs.gordon.edu/courses/cs211/ATMExample/UseCases.html

OWASP. (2015). Application Threat Modeling. Creative Commons 3.0 License. Retrieved from https://www.owasp.org/index.php/Application_Threat_Modeling#STRIDE



