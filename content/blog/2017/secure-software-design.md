title=Secure Software Design 
date=2017-02-05
type=post
tags=blog
status=published
~~~~~~

## Least privilege

Architecture and Design Considerations for Secure Software by Software Assurance says that least privilege is a principle that each component, including components from the outside world and components embedded into the program, and every user of the system, use the least set of privilege necessary to accomplish desired tasks and objectives. The objective of employing least privilege principle is to reduce the number of actors (components and users) in the system who are granted high levels of privilege, and the duration of time each actor can hold onto those privileges.

#### Benefits

A benefit for employing the least privilege principle manifests in the way project stake holders (programmers, system administers etc..) look at security measures. The military has a saying’ - “need to know bases”. Those few words encapsulate the framework of which stake holders view the project and at the core of how they handle decisions. The unintentional, unwanted, or improper use of privileges are less likely to take place since the minimum amount of privileges are granted to users and components (Langford Jeff, 2003).     

A benefit which does not come much as a surprise is that it is fundamentally and practically harder to reduce access privileges for actors when each actor is given a maximum amount of privileges at the beginning, than it when actors are given the least amount of privileges. 

#### Example

Last week we discussed requirements misuse/abuse cases and used an ATM machine as an example. This week I will use the ATM machine again to explain how least privilege principle is employed and the reasons for using the principle. An ATM is made to be simple. Customers are allowed access to deposit, withdrawal, transfer, and inquiry. Customers cannot communicate with their respective bank edit their profiles, edit bank pin, change username, edit account and routing number. Employing this principle limits the damage that can result from an accident or error.

## Don’t expose vulnerable or high-consequence components

When you host a large gathering at your home chances are that you will not leave a large ward of cash laying in the sitting room, or your passport visa along with your social security number on the kitchen table. These are high-consequence items that are being exposed to a large group of not very well unknown people. In software development a program usually hosts sensitive business data, personal identifiable information (PII), sensitive program executables and functions. These high consequence components should not be exposed to non-consequence components, meaning that high-consequence components should be stored separately from non-consequence components. The passport visa, social security number, and the large ward of cash should be placed in a boxed safe stored in a low traffic area such a locked bedroom. 

#### Benefits and Examples

Not exposing vulnerable or high-consequence components means that you are actively and deliberately isolating trusted entities from untrusted entities. For example, program data executables and configuration data would be stored in a different location with the assumption that environment data is not trustworthy. This deliberate isolation of trusted entities from untrusted entities naturally reduces the attack surface and here is why. Going back to our house analogy, the act of removing passport visa and social security number along with the large ward of cash from the kitchen to a safe box in a locked bedroom drastically reduces the attack surface to one point of entry. It is easier to keep a recorded log of activities in a bedroom compared to an open concept kitchen. As a result, the attacker has a harder time locating and gaining access on vulnerable or high-consequence components because the attacker is left guessing where vulnerable/high-consequence components could be held his given limited resources to operate.

## Complete mediation

Complete mediation design principle is a mechanism of which a software system systematically checks required access an object has each time that object attempts to access any type of resource. A reference monitor is a piece of software that checks every reference made by subjects to objects (Implementing Complete Mediation, by Schneider). To find out why reference monitor is critical for complete mediation, we use a simple example, if the access control rights of a subject are decreased after the first time rights are granted and the system does not check the next access to that object, security vulnerabilities can occur throughout the system.

**Note:** When we say object, it can mean the various components that encompass the whole system (including sub-components), outside plugins or software, users etc.

#### Benefits

Software Assurance (SwA) Pocket Guide Resources in an article titled Architecture and Design Considerations for Secure Software stated it accurately writing that complete mediation is the “primary underpinning of the protection system” (Software Assurance, 2008). The consistent evaluation of subject’s access to objects not only ensures that no permission violations can occur, but also makes it easier to log successful and unsuccessful authentication attempts on resources. A benefit would then be that during a security breach, swift actions can be taken to mitigate damage since access to various components is accurately logged. 

#### Example

This past fall 16’ I was a Software Developer Intern for a startup creating batteries for electric vehicles. My role as a back-end developer exposed me to Amazon Web Services (AWS) cloud ecosystem. AWS employs complete mediation. In AWS ecosystem each user, AWS tool, and outside plugins are given various levels of access. The AWS administrator controls the amount of access each entity possesses. To give an example, for the Lambda Function to filter data coming from our API Gateway and then store the appropriate data in DynamoDB, the Lambda Function had to get appropriate permission from DynamoDB by triggering the two together. In order for the API Gateway to send raw data in Lambda Function, Lambda Function and API Gateway both had to be triggered together with the appropriate access. Lastly, the API Gateway had to establish appropriate access level with an outside entity where the data would be generated which in our case was customer purchase orders using a third party platform. Any change in access level along the chain causes the entire system to break. 

## Psychological acceptability

Psychological acceptability design principle is another way of saying software system design should be intuitive to any user, particularly the client side. In my view, to achieve an easy to understand or intuitive user interface (UX), the design should also follow established guidelines for supporting accessibility of disabled people. There are more than one billion people with various disabilities all around the world, of whom approximately 285 million are visually-impaired and 360 million hearing impaired (Rezaei A. Yashar, Heisenberg Gernot, and Heiden Wolfgang, 2014). With this approach, impaired users not only are able to easily apply protection mechanisms correctly, regular users are able to do so as well, increasing the security of the system.   

#### Benefit

The overarching benefit that derives from employing psychological acceptability design principle is the drastic reduction of mistakes on the part of the user. The reduction of mistakes in tern translate to a more robust secure system.

#### Examples

The user must become involved in security decisions at some point. Either when the system is loading or when the system attempts a privileged operation. To use an everyday example, today it seems every company is using an interactive map for something. In order for an application to retrieve a user’s geolocation, by law the application has to prompt the user for access. Another example is whenever a user installs an application from an outside source, they are to be prompted for access of resources to be used and how they are to be used. 

## Minimize the number of high-consequence

The design principle of minimizing the number of high-consequence components from security risk employs the least privilege principle, separation of privilege, duties, and roles and separation of domains. The key concept of the design principle is to reduce the number of high-consequence components from risk. For example, to separate environments that are not trusted from trusted environments, and reduce the number of entities interacting with the high-consequence components. 

#### Benefits and Example

The implementation of least privilege to minimize the number of high-consequence ensures the number of actors in the system that are granted high levels of privilege is reduced strengthening overall security. Another benefit derived from minimize the number of high-consequence is that the separation of domains makes it easier to implement separation of privileges, duties, and duties (Software Assurance Pocket Guide Series).

**Sources:**

Gegick Michael and Barnum Sean. (2005-2007). Least Privilege. Cigital [PDF file]. Retrieved from https://www.us-cert.gov/bsi/articles/knowledge/principles/least-privilege

Langford Jeff. (2003). Implementing least Privilege at your Enterprise. SANS Institute InfoSec Reading Room [PDF file]. Retrieved from https://www.sans.org/reading-room/whitepapers/bestprac/implementing-privilege-enterprise-1188

Mahizharuvi and Alagarsamy. A Security Approach in System Development Life Cycle. Dept of MCA, Computer Center (Vol. 2) [PDF file]. Retrieved from http://www.ijcta.com/documents/volumes/vol2issue2/ijcta2011020204.pdf

Micheal C.C, Gegick Michael, and Barnum Sean. (2005-2007). Complete Mediation. Cigital. Retrieved from https://www.us-cert.gov/bsi/articles/knowledge/principles/complete-mediation 

Rezaei A. Yashar, Heisenberg Gernot, and Heiden Wolfgang. (2014). User Interface Design for Disabled People Under the Influence of Time, Efficiency and Costs. Institute of Visual Computing Bonn-Rhein-Sieg [PDF file]. Retrieved from https://www.researchgate.net/profile/Gernot_Heisenberg/publication/262601817_User_Interface_Design_for_Disabled_People_Under_the_Influence_of_Time_Efficiency_and_Costs/links/02e7e5384c1486f3ee000000.pdf

Software Assurance Pocket Guide Series. 2012. Architecture and Design Considerations for Secure Software. Building Security in Software Assurance (Vol. V) [PDF file]. 

Software Assurance. (2008). Enhancing the Development Life Cycle to Produce Secure Software. A Reference Guidebook on Software Assurance (Version 2.0) [PDF file]. Retrieved from http://www.cis.upenn.edu/~lee/10cis541/papers/DACS-358844.pdf

Schneider B. Fred. Implementing Complete Mediation. Retrieved from http://www.cs.cornell.edu/courses/cs513/2004SP/NL05.html 
