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



## Identity and Access Management
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



