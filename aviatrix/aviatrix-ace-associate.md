# Aviatrix ACE Multicloud Network Associate

<details> 
<summary><h2>Identify the Characteristics of On-Premises Data Centers vs. Cloud</h2></summary>
  
- On-premises data centers:
  - Physically located within an organization's premises, are fully owned, operated, and maintained by the organization, encompassing all hardware, software, and networking equipment
  - Maintain full control over the infrastructure, encompassing servers, storage, networking devices, and security systems, allowing for customization and configuration tailored to their specific needs and preferences
  - Capital Expenditure (CapEx)
  - Scalability in on-premises data centers is hindered by physical limitations, leading to time-consuming processes like purchasing hardware and provisioning new circuits
  - Organizations control, own, and manage all aspects of security and compliance standards within their data centers. It includes responsibilities such as implementing physical security protocols, firewalls, intrusion detection systems, and encryption protocols for data protection
  - Maintenance tasks, including hardware repairs, software updates, and system monitoring, are internally managed by IT staff or outsourced to third-party service providers, with organizations accountable for ensuring the uptime, reliability, and performance of the data center infrastructure
- Cloud computing services:
  - Hosted in remote off-premises data centers by third-party vendors, are subscribed to by organizations on a pay-as-you-go basis, eliminating the need for owning and maintaining physical infrastructure
  - Cloud providers oversee and administer the underlying infrastructure, encompassing servers, networking, storage, and virtualization technology, while users, although having limited control over physical hardware, can configure and manage resources via a web-based interface or API
  - Operational Expenditure (OpEx)
  - Cloud services provide virtually limitless scalability, enabling organizations to adjust resource levels in response to demand fluctuations. Users can provision additional resources on-demand or automatically scale according to predefined rules or triggers
  - Cloud service providers (CSPs) provide security as a shared security model. The cloud shared security model divides security responsibilities between the cloud service provider (CSP) and the customer, varying based on the service model (IaaS, PaaS, SaaS). CSPs are responsible for securing the cloud infrastructure and platform, while customers are tasked with securing their data, applications, and access management. This collaborative approach ensures both the infrastructure and the data it hosts are comprehensively protected against cyber threats
  - Cloud Service Providers (CSPs) provide maintenance and support by regularly updating and patching infrastructure and platforms to ensure the security and performance of the underlay infrastructure they own. They also offer customer service and technical support to address issues, provide guidance, and ensure optimal service utilization. This proactive approach helps minimize downtime and enhance the overall user experience. Users/customers, on their part, are responsible for managing their data, implementing security measures like encryption, and controlling access to their applications and services. This partnership ensures a smooth, secure cloud experience with minimized downtime and enhanced security

</details>

<details> 
<summary><h2>Describe the Differences Between Private, Public, and Hybrid Clouds</h2></summary>

- On-prem infrastructure: Data Center, Very slow to respond to DevOps. Consists of physical and virtual resources within an organization’s own facilities, providing high security and control but requiring significant investment and ongoing maintenance
- Private Cloud: Single tenant cloud computing, Running on-prem infra. Provisioned for exclusive use by a single organization. It should provide capabilities such as on-demand self-service, broad network access, resource pooling, rapid elasticity, and measured service. Managed internally or by a third party, or some combination of them, ideal for sensitive data handling. It may exist on or off premises
- Hybrid Cloud: Public Cloud and Private, Cloud cooperating together. These combine on-premises or private clouds with public clouds
- Public Cloud: Multiple tenants, Hosted by Cloud Service Providers (CSP), Shared Infra. Operated by third-party providers, public clouds provide scalable and shared cloud computing resources accessible over the internet
  
<br />

- SaaS: service that is used for the pure consumption of software. You have no control and, therefore, no responsibility for the application - for example, Microsoft 365 or Salesforce
- PaaS: service where services are managed for you. You end up with a reduced level of control. For example, you can run a relational database service or platform without needing to install the underlying binaries or be responsible for hardening it, patching it, or even ensuring its uptime. You just need to bring your own code
- IaaS: service is where the CSP takes responsibility for the compute, storage, and networking service. The CSP abstracts the hypervisor and gives you access to the guest Virtual Machine (VM) or compute instance. You are responsible for the OS on that VM and all the libraries, middleware, and applications on that VM

</details>

<details> 
<summary><h2>Outline the Importance of Edge Computing, Hybrid Cloud and Multicloud</h2></summary>

- Public Cloud: Serves as the cornerstone of this ecosystem, offering an array of networking and security services to support crucial business workloads hosted within its infrastructure. Despite the public cloud's many advantages, certain business use cases demand direct connectivity to on-premises resources
- On-Premises Resources: These include existing data centers, legacy branch offices, SD-WAN branches, colocation facilities (colo), and IoT devices (sensors and devices that collect data and communicate with the cloud for real-time insights and automation). These resources can connect securely to the public cloud using various connectivity methods. All these resources combined are categorized as Edge resources as well. On-Prem resources are important due to compliance (Federal requirements and GDPR regulations) and legacy systems (integration with existing on-prem systems for certain businesses)
- End User Devices: End User Devices refer to the array of devices used by individuals, including employees, contractors, developers, and others. These devices encompass laptops, desktops, tablets, and smartphones, serving as the interface through which end users access and interact with cloud resources

</details>

<details> 
<summary><h2>Examine the Design Considerations and Tradeoffs For Moving to Public Cloud</h2></summary>

- Business Pain: Compliance and governance concerns, DR/BC for CSP availability, hybrid cloud connectivity costs, consumption-based bill back/show back
- Technical Pain: Performance vs Security tradeoff, advanced routing controls, security and segmentation requirements, complex setup and troubleshooting
- Key drivers for moving to public cloud: Agiility, automation, innovation, faster time to market
- Considerations when moving to the cloud:
  - Urgency of DevOps drove cloud migration, leaving network and security teams behind. Traditional networking components like routers, switches, and firewalls don't seamlessly align with the cloud's infrastructure. It's not a direct translation from on-premises to cloud; instead, the cloud offers its own suite of infrastructure services to support application development
  - From a networking and security standpoint in the public cloud, the focal point of networking and security has shifted dramatically. Unlike on-premises setups, where applications typically pass through a DMZ for security inspection, public cloud environments, with certain cloud service providers (CSPs), grant immediate internet accessibility by assigning applications a public IP address
  - Enterprises must adapt to a non-standard and inconsistent model in the cloud. Even basic networking services like route tables are managed differently by each CSP. Additionally, new services such as gateway load balancers and application gateways are introduced, with each CSP offering its distinct version alongside unique managed services for networking and security
  - Navigating this complexity while maintaining an agile and secure operational framework to meet evolving business demands poses a significant task - but it can be achieved by using a born-in-the-cloud vendor like Aviatrix
- Design Considerations:
  - Considerations with Building: Cloud Service Providers (CSPs) offer foundational constructs such as Virtual Private Clouds (VPCs), route tables, subnets, and compute instances. However, it's up to the user to determine how to use and integrate these components to accommodate their applications effectively. Unfortunately, there's a lack of standardized best practices or reference architectures for networking
  - Considerations with Operations: CSPs currently lack a comprehensive toolkit for managing networking environments efficiently. While basic tools like flow logs exist, their export capabilities are often limited. There is a cost associated with processing and storing the logs. Visualization options must be improved. Furthermore, there is a notable absence of tools tailored to troubleshoot network issues rapidly
  - Considerations with Growing: Consider a scenario where your business requires expansion from a single region to multiple regions or even to another cloud—a trend rapidly gaining momentum. Unfortunately, none of the CSPs is particularly incentivized to assist in expanding to other clouds, as providing multicloud support doesn't align with their best interests. In fact, some CSPs actively avoid using the term "multicloud" altogether

</details>

<details> 
<summary><h2>Learn the Basic Networking Capabilities of the Primary CSPs</h2></summary>

- Cloud Service Provider (CSP) Essentials:
  - Identity and Access Management (IAM): Manage user identities and their access to resources in the cloud infrastructure. Typically involves features such as user authentication, authorization, roles, permissions, and policies
  - Core Services: Fundamental computing resources such as compute, storage, network, and database
  - Resource: Components or entities users can provision and utilise within cloud environment to run applications
  - Virtual Data Center: Logically isolated portion of a cloud provider's infrastructure that mimics the capabilities of a traditional physical data center but is entirely virtualized and managed through software
  - Dedicated Connectivity: Private, high-performance network connections between their on-premises infrastructure and the cloud provider's data centers. This typically involves options like dedicated leased lines, virtual private networks (VPNs), or direct connections such as AWS Direct Connect or Azure ExpressRoute

</details>

<details> 
<summary><h2>Recognize the need for a Multicloud Network</h2></summary>

- AWS: (Enterprise Solution) Offers a wide range of cloud services, including hosting internal applications, managing large databases, implementing ML algorithms, and deploying IoT solutions
- Microsoft Azure: (Hybrid Cloud Deployment) Emphasizes seammless integration with technologies such as Windows Server, Active Directory, and SQL Server. (Regulated Industries) Organizations operating in highly regulated industries like finance or healthcare may choose Azure for its strong emphasis on security and compliance
- Google Cloud Platform: (Big Data and Analytics) Specializes in data management and analytics, offering services like BigQuery for data warehousing and analysis, as well as ML tools like TensorFlow. (Containerised Applications) GCP's Kubernetes Engine provides a managed platform for deploying, managing, and scaling containerized applications, appealing to organizations seeking agility and scalability
- Oracle Cloud Infrastructure: A database service that appeals to industries requiring intensive computational tasks
- Alibaba Cloud: Enables businesses to expand operations into Chinese market by providing cloud services tailored for local requirements, regulations and business practices
  
</details>

<details> 
<summary><h2>Common Cloud Service Provider Networking and Security Limitations</h2></summary>

- AWS Direct Connect quotas:
  - 100 Routes per Border Gateway Protocol (BGP) session on a private virtual interface or transit virtual interface from on-prem to AWS. Advertising more than 100 routes each for IPv4 and IPv6 over the BGP session will cause the BGP session to go into an idle state with the BGP session DOWN
  -  1000 routes per BGP session on a public virtual interface
-  Azure ExpressRoute circuit:
  - Maximum of 1000 IPv4 prefixes advertised on a single ExpressRoute connection
- Network Limitations: Bandwidth Constraints, Higher Costs when exceeding predefined limits, Lack of Advanced Features (Quality of Service, traffic engineering, advanced routing protocols) 
- Cloud Provider Lock-In: Organizations become tightly integrated with a specific cloud provider's ecosystem
- Data Gravity: As organizations accumulate data within a specific cloud provider's environment, the cost and complexity of transferring data between providers increase significantly
- Security Concerns: Significant in multicloud environments where maintaining consistent and distributed security policies across different providers can be challenging
- Considerations in Building Consistent Networks: Lack of Interoperability, Complex Configuration Management, Visibility and Monitoring Challenges
- Skill Shortage and Training Needs: Cloud Networking Specialization, Security and Compliance Proficiency, Multicloud Expertise

#### Questions
1. Which of the following is a common limitation associated with cloud providers native networking solutions, particularly during operational scaling or when secure connectivity to on-premise or multicloud environments is required? Advanced routing protocols
2. What happens when organizations become tightly integrated with a specific cloud provider's ecosystem, making it challenging to migrate to alternative providers or adopt multicloud strategies? Cloud provider lock-in

</details>

