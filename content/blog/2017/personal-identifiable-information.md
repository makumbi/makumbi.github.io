title=Personal Identifiable Information (PII)
date=2017-02-4
type=post
tags=blog
status=published
~~~~~~

![Credit Card Entry Form](img/re-creditcardform.png)


Personal identifiable information or PII is practically any piece of information about someone maintained by an organization that can be used to distinguish or trace an individual’s identity. Information can include but not limited to name, social security number, date of birth as well as any other information that is linked or linkable to an individual.

PII examples are listed below by no means exhaust possibilities of information that could be considered PII. This is only meant to highlight/provide a framework as of what PII information can encompass. Examples include financial transactions, medical history, criminal history, employment history, individual ‘s name, social security number, passport number, driver‘s license number, credit card number, vehicle registration among others.

#### Figure 1 
 
![News Update form](img/re-newsupdate.png)


In figure 1, PII data that is being gathered from the form is title, first name, middle name and last name, address, email, and phone number. The purpose for the form is to allow people to subscribe for bi-weekly e-newsletter. This form asks people to enter (optionally) their addresses which is not necessary for a bi-weekly e-newsletter. If I worked for vendor and was tasked to improve security, I would first assess the impact level of storing and maintaining address information. I would conclude that the impact level of storing and maintaining address information is moderate since the expected loss of confidentiality, integrity, or availability could have serious adverse effect on individuals. As a result, I would lean on the side of cation by removing address from the form. 

#### Figure 2 

![Win $10,000,000](img/re-winmoney.png)


In figure 2, PII data that is being gathered from the form is name, address and data of birth in order to register to win $10,000,000 dollars. The fact that the form is asking for address is a slight over reach, and here is why, secure software development best practices show that a minimum number of information required to accomplish a particular task is needed - nothing more nothing less. If I worked for the vendor and was tasked to improve security, a possible way I would mitigate this is issue is by removing address from the form and instead wait until the participant has qualified to win the prize to solicit address information if it is needed. 

**Sources:**

Bjork C. Russell. ATM Simulation. Retrieved from http://www.math-cs.gordon.edu/courses/cs211/ATMExample/Interactions.html#Startup

Erika McCallister, Tim Grance and Karen Scarfone (April 2010). Guide to Protecting the Confidentiality of Personally Identifiable Information (PII). Recommendations of the National Institute of Standards and Technology, NIST Special Publication 800-122.

“Requirements Analysis for Secure Software”. Software Assurance Pocket Guide Series, Development, Volume IV Version21, May 18, 2012.


