# OCI Architect Associate

## IAM Overview
- Identity: AuthN, centralised identity lifecycle management, integration with existing identities and applications, secure and easy access
- Access Management: AuthZ, fine-grained access controls, define granular permission
- OCI IAM AuthN: Instance principals, federated identitiy, MFA, user credentials, API keys, OAuth 2.0 Tokens
- OCI IAM Components: Identity domains, users, groups, principals, dynamic groups, policies, compartments, resources, federation, network sources
- Identity domain: User population and associated configurations and security settings. Acts as a container to manage users, roles, federation, SSO, MFA
- Identity Domain Types:
  - Free: AuthN and AM. Limit of 2000 users, 2 non-Oracle apps, 3 external Identity Providers, limited feature support
  - Oracle Apps Premium: Unlimited external Identity Providers and support for Oracle Apps including hybrid IAM, limit of 6 non-Oracle apps
  - Premium: Includes all features, broad support for hybrid IAM use-cases, unlimited external Identity Providers and support for Oracle and non-Oracle apps
  - External User: provides social self-service and consent management, limited enterprise and hybrid IAM features, excludes APP catalog provisioning connectors


#### Skill Check
- In OCI IAM, which authentication method enables compute instances to access resources securely without storing credentials directly? Instance Principal
- In the context of OCI IAM and identity domains, what is the primary benefit of using separate domains for employees, business partners, and consumers? Improved security and compliance by isolating access privileges for each group
- When onboarding users to an OCI IAM identity domain, which of these methods can be leveraged? User self-service registration, sync from an external directory like AD using directory bridges, manual user creation only
- In the context of OCI IAM and RBAC, how are permissions assigned to users? Users inherit permissions based on their group memberships
- A company is setting up a new OCI environmnet and anticipates needing to manage a large number of users with fine-grained access control. It also plans to integrate on-premises or cloud-based Oracle and non-Oracle apps. Which OCI IAM identity domain type best meets these requirements? Premium


## IAM Basics
- Default domain is created by default with new account (root domain). Cannot be hidden from the sign-in page and is replicated to all regions to which the tenancy is subscribed. Default admin user is superuser
- Multiple identity domains are for isolation of admin control, security and compliance and simplified management
- Groups are collections of users who have common roles, permissions and access policy, simplifies access management and for audit and compliance
- Default groups in Identity Domains: All Domain Users and Domain Administrators
- IAM User Life Cycle: Non-existent (Create) > Activated (Activate, Modify, Delete) > Deactivated (Reactivate)
- Who can create User? Tenancy admin, Domain admin, User manager admin role, using policies
- OCI user creation can be done via Console (GUI), OCI CLI, REST API or Terraform. CSV import can be used for large number of users and groups. OCI Self-Registration Profiles are customisable registration flows for managing different user sets, approval policies, and applications
- Types of admin roles: Identity Domain admin, Security admin, App admin, User admin, User manager, Helpdesk admin, Audit admin
- Policies: `allow Subjects to Actions in Placement where Condition`
- Compartment: isolate resources. Dedicated compartments are all under root compartment. Resources from different compartments can interact with each other. Compartments can be shared across regions globally. Nested compartments go up to 6 levels deep
- Compartment Quotas: limit/control resource consumption. `set family quota name to value in location conditions`


#### Skill Check
- OCI compartment quotas has three quota policy statements: Set, Unset, and Zero. Which statement removes all access to a specific resource type within a compartment? Zero
- A company wants to grant a user the ability to create and manage applications within an OCI IAM identity domain, but restrict access to user accounts and security settings. Which predefined admin role would be MOST appropriate? App admin
- By default, which group in the OCI default domain has full access to all OCI Cloud resources? Admin Group
- In OCI IAM policies, verbs such as "inspect", "read", "use" and "manage" are used to: Define the level of permission granted on resources
- How many levels deep can compartments be nested within OCI? 6 levels



## IAM Advanced
- Child policies are inherited from parent policies
- Created policies must be attached to a compartment (or tenancy)
- A:B:C means compartment A, B and C are affected
- Conditional Policies enable more fine-grain access control, uses variables when adding conditions. Variables are hierarchically named, prefixed accordingly with either `request` (e.g. request.permission='OBJECT_CREATE') or `target` (e.g. target.bucket.name='<bucket_name>') followed by a period (.)
- Syntax for a single condition: variable =|!= value
  - `=|!=` returns true or false for every condition
  - `!=` inverts the result
- Syntax for multiple conditions























