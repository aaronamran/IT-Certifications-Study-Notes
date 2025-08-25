# OCI Foundations

## OCI Architecture
- Region: localised geographic area comrpising of one or more availability domains (AD)
- Availability domains (AD): one or more fault-tolerant data centers located within a region but connected to each other by a low-latency high bandwidth network
- Fault domains (FD): grouping of hardware and infrastructure within an availability domain to provide anti-affinity
- Has multi-cloud partnership with Azure
- Choose a region closest to your users for lowest latency and highest performance and consider data residency requirements and compliance
-  AD are isolated from each other, fault tolerant and unlikely to fail simultaneously. They do not share physical infrastructure
-  Each AD has 3 FD. FD are logical data centers within an AD. Resources placed in FD will not share single points of hardware failure
-  Replicate app and DB on each FD and also on another AD. Use Oracle Data Guard to sync data

### Skill Check
- Which statement about regions and availability domains is true? An OCI region has one or more availability domains
- Which statement about OCI is NOT true? A single fault domain can be associated with multiple availability domains within a region
- Which OCI service is NOT intended for a multicloud solution? Oracle Roving Edge Infrastructure
- Which capability can be used to protect against failures within an OCI availability domain? Fault Domain
- You have subscribed to an OCI region that has one availability domain. You want to deploy a highly available application with two servers and a 2-node database. How would you place the components to maintain the high availability of the application? Place one server and a DB node in one fault domain, and the second server and DB node in another fault domain



## Identity and Access Management (IAM)
- AuthN is who are you while AuthZ is what permissions do you have
- Identity domain is a container for users and groups, it represents a user population in OCI and associated configurations and security settings
- First create identity domain, then create users and groups inside it, then write policies (RBAC) against those groups, and policies are scoped to a tenancy, an account or a compartment. Resources are available within a compartment
- OCI assigns Oracle Cloud ID (OCID) for each resource automatically
  ```
  ocid1.<RESOURCE TYPE>.<REALM>.[REGION].[FUTURE USE].<UNIQUE ID>
  ```
- When you open an OCI account, you get a tenancy (aka account) and a root compartment. Can create compartments for isolation and controlling access. Root compartment holds all cloud resources
- Each resource belongs to a single compartment. Once it goes to compartment A, it cannot go to compartment B. It needs to be moved, or deleted and recreated
- Resources can interact with other resources in different compartments
- All compartments are global and are available in every region you have access to. Compartments can also be nested up to 6 levels deep
- Quotas and budgets can be set on compartments
- Principal is an IAM entity that is allowed to interact with OCI resources. Two types are IAM users (humans) and resources (instance principal that makes API calls against other OCI services)
- Groups are collection of users who have same access requirement to resources
- Common AuthN for cloud is using API signing key (uses a public-private key pair) to make API calls, auth tokens are Oracle-generated token strings that authenticate third party APIs
- AuthZ is done through IAM policies, which are human readable statements to define granular permissions. Everything is denied by default, so need to specifically allow
  ```
  Allow <domain_name>/<group_name> to <verb> <resource-type> in <location> where <condition>
  ```
- 
  


## Networking
- 


## Compute
- 


## Storage
- 


## Security
- 


## Governance and Administration
- 



