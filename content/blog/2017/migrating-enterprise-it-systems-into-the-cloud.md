title=Why a business should consider migrating its enterprise IT systems into the cloud infrastructure
date=2017-03-26
type=post
tags=blog
status=published
~~~~~~

You work for a startup which in a short amount of time grew into a medium size company because it acquires auctioned vehicles, repairs and rents them out to people for below market rates. The company is called Auto Service LLC. Auto Service LLC is in the automotive service industry and has carved out a niche in the middle eastern region of the country planning to expand into the southern region in the coming months. Since its customers are free to drive the vehicles anywhere in the country, it tracks each fleet by GPS and also gathers and stores vehicle diagnostics data including how fast the vehicle is traveling, gas in the vehicle, where the vehicle is located, condition of the vehicle, and who is driving the vehicle at a given time. 

The Auto Service LLC manages all the computing resources in house (i.e networks, servers, storage, applications, and services). It has a dedicated staff around the clock that monitor and enforce security controls on facilities, networks, applications, and storage access controls among other responsibilities. As an example, a physical security perimeter is in place to prevent unauthorized access, in addition to physical entry controls to ensure authorized personnel have access to areas containing sensitive information. Auto Service LLC also conducts extensive background checks on its personnel before granting them access to secure areas. 

We prepare a recommendation to board members to integrate cloud computing architecture into Auto Service LLC’s business operations. The objective will be to outline a specific service model and deployment model(s) that fits the needs of the organization discussing possible security concerns, risks and how they can be mitigated in an effort of convincing board members to get on board.  

### Migrating to Cloud Computing Infrastructure

Auto Service LLC has plans to expand its operations into southern states of the country which is going to introduce challenges as to how critical infrastructure will be securely managed in order to maintain confidentiality, integrity, and availability of data and services. In order to maintain availability cold, warm and hot sites would have to be established which in a long run can be very costly to the organization’s bottom line. In addition, regardless of whether resources are being used or not, computing infrastructure (networks, servers, storage, applications, and services) have to be operational 24/7 once again impacting the organization’s margins.

An integration of cloud computing, in particular, Infrastructure as a Service (IaaS) will successfully turn the organization into a cloud customer. The benefits IaaS bring to the organization will be felt from day one. No capital investments will be required using a service provider because as we discussed before servers, storage and network hardware are located and maintained at the provider’s site. This leads to another benefit which is that Auto Service LLC will only pay for only what is needed providing the necessary flexibility to scale as the company grows and scale back if the company downsizes. IaaS consumers are provisioned with the capabilities to access these computing resources, and are billed according to the amount or duration of the resources consumed, such as CPU hours used by virtual computers, volume and duration of data stored, network bandwidth consumed, number of IP addresses used for certain intervals (Workgroup leaders, 2012). Lastly, business continuity is maintained given the high availability nature of IaaS consolidating disaster recovery infrastructure, further reducing costs and increasing manageability (StateTech Staff, 2014).

### Cloud Computing Security Concerns

Migrating to the cloud computing infrastructure brings with it a share of security concerns that have to be discussed. The utilization of IaaS means that security responsibilities are shifted between Auto Service LLC and cloud provider. The cloud provider is responsible for the supply of basic IT resources in regards to physical infrastructure, house machines, networks and disks. However, Auto Service LLC is responsible for providing and maintaining the operating system and the entire software stack needed to run applications. Security concerns particularly arise when we discuss about how the provider will maintain confidentially, integrity and availability of data and services. We trust that security policy controls will be put in place to enforce security best practices, but as we know that effort is never guaranteed. For example, it can be unclear as to the type of access controls a provider implements to restrict unauthorized access. Also how rigorous are personnel background checked to mitigate malicious insider attacks. What steps are being taken to ensure that interrupted availability does not occur.

Security concerns do not only apply to the cloud provider because security responsibilities are shared in a IaaS service model. Security means nothing if the cloud provider has hardened its security posture and the customer has a hands off approach to security. Auto Service LLC has to ensure patch management practices on operating systems and software stack are up to date and follow security best practice. Robust incident management plans should be clearly documented with a dedicated team which has been provided adequate tools and training. Each staff member has to undergo annual security training tailored to their roles in the organization.

### How to Address Security Concerns

Steps can be taken to address security concerns of cloud provider’s ability to ensure confidentiality, integrity and availability of data and services. These steps vary in nature but each requires a holistic approach on the customer point of view. Auto Service LLC should be focused on the network, physical environment, auditing, authorization, and authentication considerations when assessing a provider’s capabilities. Questions to ask are listed below -

1. Is it clear whether responsibility for applications running on cloud infrastructure lies with the consumer or with the provider?  
2. Where the responsibility lies with the provider, does the SLA make the provider's responsibilities clear and require specific security provisions to be applied to each application and all data?  
3. Does the service provider have facilities in place to ensure continuity of service in the face of environmental threats or equipment failures?
4. Can the cloud service provider demonstrate appropriate security controls applied to their physical infrastructure and facilities?  
5. Does the network provide the consumer with logging and notification?  
6. Is consumer network access separated from provider network access?  
7. Is there separation of network traffic in a shared multi‐tenant provider environment?  

**Note:** These questions are only a suggestion and that more questions should be asked pertaining to effective governance, risk and compliance, management of people, roles and identities, protection of data and information, privacy controls amongst others.

### Cloud Vendor Best Suited for Auto Service LLC

The cloud Infrastructure-as-a-Service space is undergoing a shift in strategies around market leaders who include Amazon Web Services (AWS), Microsoft Azure, Visionaries, Google Cloud Platform, CenturyLink Cloud, vCloud Air from VMWare, and IBM (SoftLayer). These leaders may not be best providers for Auto Service’s specific need, and they may not serve some use cases at all, but they have a track record of successful delivery, significant market share and lots of customers that can provide references (Thor Olavsrud, 2015). For our recommendation, we compared Amazon Web Services and Microsoft Azure and believe AWS is best suited for Auto Service’s fleet management enterprise. Observing the past, we know that AWS’s roots are primarily IaaS, because its storage footprint and the demand of supporting Simple Storage Service, Linux, Firefox and SimpleDB. Azure’s initial focus was primarily PaaS due to the launch of SQL 2008, SharePoint and .Net integration. AWS is VM-first while Azure is services-first. Azure has a clear advantage for customers looking for PaaS but our focus in on IaaS (Jo Peterson and Michael Goodenough, 2015).

### Deployment model(s)

In order to understand the deployment model(s) that best suit Auto Service LLC, it is a good idea to first take a step back to understand the different types of deployment models and get a sense of their respective security postures.

A community cloud serves a group of Cloud Consumers which have shared concerns such as mission objectives, security, privacy and compliance policy, rather than serving a single organization as does a private cloud. A community cloud may be managed by the organizations or by a third party, and may be implemented on customer premise or outsourced to a hosting company (NIST Cloud Computing Reference Architecture, 2011). The attack surface is spread out depending on the number of tenants which is a concern because host hijacking vulnerabilities are increased. Special attention on access control and data management has to be clearly documented and readily available to customers.

The public cloud infrastructure is provisioned for open use by the general public. It may be owned, managed, and operated by a business, academic, or government organization, or some combination of them. It exists on the premises of the cloud provider. Customers have no exclusive access to usage of infrastructure and computational resources.

The hybrid cloud infrastructure is a composition of two or more distinct cloud infrastructures (private, community, or public) that remain unique entities, but are bound together by standardized or proprietary technology that enables data and application portability.

Private cloud infrastructure gives a cloud customer’s organization the exclusive access to and usage of infrastructure and computational resources. It can be managed by either the cloud customer, a third party, and may be hosted on the organization’s premise. It is important to note that private cloud infrastructure is the most secure and provides the customer the most control. We recommend that Auto Service LLC’s business objectives will best be served by the use of private cloud infrastructure.

### Conclusion

Auto Service LLC has successfully managed to grow the into a middle side company and is now in talks to expand into the southern states of the country. Now more than ever there needs to be a close evaluation on the sustainability and scalability capabilities of the company when it comes to its enterprise IT systems. This report lays out current trends in cloud computing security and provides recommendations for a cloud computing architecture for adoption.

Infrastructure as a Service (IaaS) best addresses Auto Service’s current business of fleet management and its desire to cut costs on physical infrastructure housing servers, storage and network hardware. IaaS allows Auto Service to pay for only what is needed providing the necessary flexibility to scale as the company grows and scale back if the company downsizes. IaaS also enables Auto Service to focus on what they do best which is to deliver quality service to customers.

On the other hand, risk considerations have to be migrating to a cloud computing infrastructure. The utilization of IaaS essentially shifts security responsibilities between Auto Service LLC and cloud provider. Concerns particularly arise when we discuss about how the provider will maintain confidentially, integrity and availability of data and services. We trust that security policy controls will be put in place to enforce security best practices, but as we know that effort is never guaranteed. Questions that should be asked include but not limited to the following; Does the service provider have facilities in place to ensure continuity of service in the face of environmental threats or equipment failures? Can the cloud service provider demonstrate appropriate security controls applied to their physical infrastructure and facilities? Does the network provide the consumer with logging and notification?  

Given all the information presented in this recommendation, Amazon Web Service’s Information-as-a-Service with a deployment of private cloud model will ensure Auto Service maintains its lean growth strategy without having to contemplate how enterprise IT systems will be secured or how profit margins will be increased.

#### Citations 

Fang Liu, Jin Tong, Jian Mao, Robert Bohn, John Messina, Lee Badger and Dawn Leaf. (2011). NIST Cloud Computing Reference Architecture: NIST Special Publication 500-292. Gaithersburg, MD. Computer Security Division Information Technology Laboratory National Institute of Standards and Technology.

Mell Peter and Grance Timothy. (2011). The NIST Definition Cloud Definition: NIST Special Publication 800-145. Gaithersburg, MD. Computer Security Division Information Technology Laboratory National Institute of Standards and Technology.

Peterson Jo and Goodenough Michael. (2015). AWS or Azure? 7 Decision Points. Channel Partners. Retrieved from: http://www.channelpartnersonline.com/blogs/peertopeer/2015/12/aws-or-azure-7-decision-points.aspx

StateTech Staff. (2014). 5 Important Benefits of Infrastructure as a Service: The benefits of the cloud extend far beyond cost savings. StateTech. Retrieved from: http://www.statetechmagazine.com/article/2014/03/5-important-benefits-infrastructure-service

Thor Olavsrud. (2015). Top Cloud Infrastructure-as-a-Service Vendors. Chief Information Officers Magazine. Retrieved from: http://www.cio.com/article/2947282/cloud-infrastructure/top-cloud-infrastructure-as-a-service-vendors.html#slide1

Workgroup leaders. (2012). Security for Cloud Computing: 10 Steps to Ensure Success. Cloud Standards Customer Council.






