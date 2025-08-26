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

#### Skill Check
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
- Tenancy admin is the person who creates and manages an account
- Best practice is create an OCI admin (can be set of users) and group them all under OCI-admin-group, then write policies for this group and they all operate under a dedicated compartment


#### Skill Check
- Which is NOT a component of OCI Identity and Access Management? Network Security Group
- Which statement about OCI compartments is NOT true? It is a best practice to create all your resources in the root compartment
- How is a resource in OCI identified? With OCID
- Which Identity and Access Management component helps to organise multiple users into a team? Groups
- Which statement about OCI Identity and Access Management is true? It enables you to control access for a group of users
  


## Networking
- Virtual Cloud Network (VCN) is a private SDN used for secure communication for instances
- VCN has an address space (denoted in a CIDR notation) that can be broken down into subnetworks
- Computer instances are instantiated in these subnetworks
- Internet gateway which is massively scalable and highly available is used for communication to anything on the internet (bidirectional)
- NAT gateway is a router for NAT as a service (unidirectional, from private subnet to internet)
- Service gateway lets resources in VCN securely access public OCI services without using internet or NAT gateway
- Dynamic routing gateway is a virtual router that provides a path for private traffic between your VCN and destinations other than the internet (on-premises environment)
- Route table is used by VCN to send traffic out of VCN to the internet, on-prem network or peered VCN. It consists of a set of route rules, where each rule provides a destination CIDR block and route target. Route target is the next hop for the traffic that matches the destination CIDR block
- Traffic within the VCN subnet is automatically handled by the VCN local routing
- Priority routes are based on CIDR blocks that are bigger or more specific
- Peering has 2 possible scenarios: Local peering (within the same region) and remote peering (two networks in different OCI regions)
- Dynamic Routing Gateway v2 is for handling large number of networks (max 300 VCNs) and does not need to use a local peering gateway for maintaining point-to-point connectivity 
- Security list are firewall rules associated with subnet. It applies to all instances in or out of the VCN
- Network Security Groups (NSG) apply to individual vNICs, it is possible to have 2 instances in a single subnet
- Load Balancer aka Reverse Proxies would proxy traffic from clients to various backend servers
- Layer 7 Load Balancer understands HTTP/S. Comes in 2 different shapes: Flexible shape (define minimum speed, maximum speed and range) and Dynamic shape (predefined shapes: micro, small, medium, large). Can be public or private. Has higher level intelligence due to packet inspection
- Layer 3 & 4 Network Load Balancer understands TCP, UDP and ICMP. Can be public or private. Much faster than HTTP Load Balancer, has lower latency. Prioritises performance

#### Skill Check
- Which VCN component blocks inbound traffic, but enables outbound traffic to the internet? NAT Gateway
- Which OSI layer traffic is supported by the OCI Network Load Balancer? Layer 4 (transport)
- Which statement about a Virtual Cloud Network (VCN) is true? A VCN can reside only in a single region but can span multiple availability domains
- Which component is NOT created by default with the creation of a Virtual Cloud Network? Default Local Peering Gateway
- Which statement about Virtual Cloud Network (VCN) peering between two VCNs is NOT valid? A VCN peering connection is a VPN-based connection
  


## Compute
- OCI Compute Service provides VMs (shared, multi-tenant), Bare Metal servers and Dedicated Host (don't share VM host with other customers) with scalability, high performance and lower pricing
- Flexible shape means can choose own cores, CPU processors and memory. Has T-shirt sizing (S, M, L). Processor options: AMD, Intel, Ampere (ARM)
- Preemptible VMs are low cost, short lived VMs suitable for batch jobs and fault tolerant workloads and are 50% cheaper
- An instance is a compute host which has several dependencies. An OCI region is comprised of multiple ADs (data centers). First dependency is Virtual Cloud Network divided into subnets. Another dependency is boot volume, boot disk and block volumes
- Live migration is to migrate VM to another host in data center without rebooting
- Vertical scaling: scale-up or scale-down, new shape must have same hardware architecture, requires downtime
- Horizontal scaling (Autoscaling): add more VMs of the same shape, scale-out or scale-in
- VMs : Hardware > Hypervisor > VM > OS > Library/dependencies > Application
- Containers : Hardware > OS > Container Runtime (Docker) > Container > Library/dependencies > Application
- Container orchestration: Process of automatically deploying and managing containers
- Docker is used to manage and build containers, Kubernetes links containers running on multiple hosts and orchestrates them
- Pod is a group of one or more containers with shared storage and network resources and specification file on how to run the containers. Smallest unit of compute
- Oracle manages control plane nodes while customer manages the worker plane nodes
- Oracle Container Engine for Kubernetes (OKE) Clusters includes Basic Clusters and Enhanced Clusters
- Managed nodes: you are responsible for managing managed nodes, upgrading Kubernetes and managing cluster capacity, and you can create managed nodes and node pools in both basic clusters and enhanced clusters
- Virtual nodes: provides serverless Kubernetes experience. Kubernetes software is upgraded including security patching. You can only create virtual nodes and virtual node pools in enhanced clusters
- OCI Container Instances eliminates operational complexities (manage VMs and servers, OS patching, container runtime updates) by directly running container images. Environment variables, resource limits and startup options can be specified
- Oracle Functions: event driven architecture. Function runs in container and is billed only for the duration the function runs and can be executed in parallel

#### Skill Check
- Which processor type is NOT available for the OCI Compute service? Snapdragon
- What is the primary purpose of OCI Functions? To execute code in response to events or HTTP requests
- Which type of storage is associated with instances in the OCI Compute service? Block storage
- Which 2 parameters can be customised when creating a flexible shape compute instance? Amount of memory & number of OCPUs
- Which statement about the working of autoscaling in an instance pool is true? It automatically provisions and removes instances in an instance pool



## Storage
- Questions to answer: Persistent vs non-persistent storage? Type of data stored? Performance? Capacity? Durability? Connectivity? Protocol?
- Local NVMe: locally attached storage, NVMe SSDs, for performance sensitive applications due to high IOPs
- Block Volume: take locally stored, attached storage and move it to a remote network server to make it persistent and durable. The data is managed as fixed-sized blocks, create a partition, create a filesystem, mount the filesystem
- File Storage: shared file storage system. Managed as files and directories, does not need partitioning, still needs mounting
- Object Storage: for storing any kinds of data available on web. Uses HTTP verbs
- OCI Data Migration Services: Data Transfer Disk > send disks to Oracle and they migrate data for you. Data Transfer Appliance > use a much larger appliance to send data
- OCI Object Storage: internet-scale, high performance storage platform. Data is managed as objects, ideal for unstructured data. Has regional or public service with multiple storage tiers
- OCI Object Storage Scenarios: Content repository, stores unstructured and semi-structured data, used for big data analytics and as archive/backup
- Object are key/name value pairs. Can have metadata. Objects are stored in buckets and have unique names. Has a flat hierarchy, and folder structure is simulated by using prefixes. Namespace (account name) is a top-level container for all buckets/objects
- Standard tier (hot): fast, immediate access. Most recent copy of the data. Instantaneous retrieval, cannot be downgraded
- Infrequent access tier (cool): costs lower than standard tier, minimum retention requirement: 31 days. Has retrieval fees
- Archive tier (cold): seldom or rarely accessed data, minimum retention requirement: 90 days. Objects need to be restored before download. Restore time: 1 Hour, download time: 24 hours. Cannot be upgraded
- Block Volume: can create and attach disks, detach and delete disks and keep data even after instance is deleted
- Lower Cost tier: Large sequential I/O workloads, 2 IOPS/GB
- Balanced tier: Balanced choice for random I/O, 60 IOPS/GB
- Higher Performance tier: Most I/O-demanding workloads, 75 IOPS/GB
- Ultra High Performance: Highest I/O-demanding workloads. 90-225 IOPS/GB
- Replication of Block Volumes: replicated across regions for disaster recovery, migration or business expansion
- Volume Groups: group volumes together for easy management and time consistent backups
- File Storage: hierarchical collection of documents organised into named directories
- In the cloud, distributed file systems used are NFS for Linux and SMB for Windows
- Use cases of File Storage: Oracle Apps Lift and Shift, General purpose file systems, micro services and containers
- OCI File Storage: Shared storage for compute instances, supports NFSv3 distributed file system, data protection: snapshots, security: data-at-rest and in-transit encryption


#### Skill Check
- You want to store the backup of a database in cloud storage for an extended period at the lowest storage cost. Which object storage tier would you use for storing these backup files? Archive
- What feature of the OCI Block Volume service ensures data durability and protection against hardware failures? Replication
- You have created an Object Storage bucket of Archive tier. Which statement is NOT valid for the Archive Storage tier? The Archive storage can be upgraded to Standard storage
- In the OCI Object Storage Service, what is the primary purpose of a pre-authenticated request URL? To provide temporary and secure access to a specific object
- You have an extremely high performance database workload that requires at least 90 IOPS/GB and 90k IOPS per volume. Which OCI Block Volume performance level can be used to meet this requirement? Ultra High Performance



## Security
- Shared security model: Oracle manages infra, customer manages OS to app and data
- Defense-in-depth layers (highest to lowest layer):
  - Infra protection > DDoS protection, WAF, Security Lists/NSG, Network Firewall
  - Identity and Access Management > IAM, MFA, Federation, Audit
  - OS and Workload Protection > Shielded Instances, Dedicated Host, Bastion, OS Management
  - Data Protection > Vault Key Management, Vault Secrets Management, Data Safe, Certificates
  - Detection and Remediation > Cloud Guard, Security Zones, Threat Intel, Vulnerability Scanning
- Oracle Cloud Guard: automated cloud security posture. Specify targets (resources), detect issues, problems and potential security issue and responders do corrective actions
- Security Zone: cloud compartment where security cannot be disabled. Security zone recipe enforce specified policies
- Security Advisor: service that unifies security zone, cloud guard and other cloud capabilities
- Symmetric Encryption: use same key to encrypt and decrypt messages
- Asymmetric Encryption: public key to encrypt messages, private key to decrypt messages
- OCI Vault: centrally manage encryption keys and secrets (passwords, credentials, SSH-keys, auth tokens)
- Envelope Encryption (two-tiered hierarchy): master key encrypts data key, data key encrypts storage. Deletion of master key means no way to recover data, that's why have soft delete for keys with 7-day gap


#### Skill Check
- What is the primary purpose of the OCI Vault service? To store and manage encryption keys and secrets
- Which of the following is NOT a component of the OCI Vault service? Database backup
- What is the main advantage of using OCI Security Zones when deploying resources in your cloud environment? Ensuring adherence to security best practices and policies
- Which option is NOT a component of Oracle Cloud Guard? Targets
- In the OCI shared security responsibility model, who is responsible for securing the underlying cloud infrastructure? Oracle



## Governance and Administration
- Pay as you go (PAYG): need to pay for VM even if not in use
- Consumption Based Pricing: charged per consumed resource for serverless and functions
- Annual Universal Credits: must use credits within 12 months
- Bring your own license (BYOL): apply current on-prem Oracle License to equivalent IaaS and PaaS cloud services
- OCI Budgets: track costs in tenancy, setup alerts, cost analysis, usage reports, compartment quotas
- Cloud Advisor analyses cloud resources and provide recommendations to maximise cost savings and optimise performance, security and availability
- Tags are key value pairs to organise resources
- Free-form Tags: basic, comprises of key and value only, no defined schema or access restriction
- Defined Tags (recommended): more features and control, contained in namespaces, defined schema, secured with policy
- Oracle Support Rewards: customers earn Support Rewards that are then applied as a form of payment for their software update licenses. 


#### Skill Check
- In OCI, what can you set up to receive notifications when budget thresholds are reached? Email alerts
- In OCI, what is the key difference between service limits and compartment quotas? Service limits are set by Oracle for a tenancy or region, while compartment quotas are user-defined for specific compartments
- Which type of traffic is charged under data transfer costs in OCI? Egress to the internet is charged
- Which is NOT a factor that influences pricing in OCI? Choice of OCI region
- Which is NOT a supported OCI pricing model? Sovereign subscriptions

  

## Sample Exam Questions
- Which component of OCI Networking Service provides a private connection between a VCN and an on-premises network? Dynamic Routing Gateway (DRG)
- What is the primary purpose of the Network Security Group (NSG) in OCI Networking Service? To control traffic flow between specified resources within a VCN
- What is the term used to describe the combination of an instance's shape, base iimage, and metadata in OCI compute service? Instance Configuration
- What is the primary purpose of OCI Functions? To execute code in response to events or HTTP requests
- What feature of OCI Object Storage Service enables users to automatically move objects between storage tiers based on predefined rules? Object Lifecycle Management
- Which performance level is NOT available in OCI Block Volume Service? Low Performance
- Which of the following features is NOT provided by OCI Security Zones? Storing and managing encryption keys and secrets
- Which OCI service is responsible for securely storing and managing encryption keys and secrets? Vault
- Which factors does NOT impact the cost of running a virtual machine instance in OCI? The region used by the VM instance
- Which of the following best describes the relationship between OCI Regions and Availability Domains? An AD is part of a region
  
