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
- Syntax for multiple conditions: `any|all {<condition>,<condition>,...}`. any is logical OR, and is logical AND
- Permissions granted cumulate as you go from inspect > read > write > manage
- Tag-Based Access Control allows defining policies with tags that span compartments, groups, and resources. Can scope access based on the tags applied to a resource
- Network sources controls access based on IP addresses. Create set of defined IP addresses from VCN or public IP addresses, then write policies: `allow group <domain>/<group> to manage <resource> in tenancy where request.networkSource.name='corpnet'`
- Principal: Identity of caller trying to access/operate on a resource
- Resource Principal Patterns: Infrastructure (IAM service feature enables instances to be authZ actors to perform actions on service resources - Instance Principal), Stacked (Projecting one principal on top of another, a service controlling a resource, not the infra, specifies the intention of the resource - Oracle Database), Ephemeral (Using injected identifiers, a service defines who the holder of a particular credential is for a short period of time - Oracle Function)
- Dynamic Groups allows Infra, Stacked and Ephemeral resource principals to be grouped as "principal actors" which are similar to other groups. Policies permit Dynamic Group principals to make API calls against OCI services. Steps: create dynamic groups, define matching rules for memberships, write policies for providing access
- Too many policies = slower API calls = performance impact. OCI enforces limits on policies/statements. Reduced policies = better scalability
- Can consolidate group membership for same members. E.g `Allow group NetworkAdminB, NetworkAdminC to manage virtual-network-family in compartment A`. Can also explicitly list required permissions instead of general verbs like `manage`
- Object IAM enables control at object level within a bucket. Use the IAM policy variable `target.object.name` to define permissions for specific objects or object patterns


#### Skill Check
- When creating a dynamic group in OCI IAM, what defines the membership criteria? Matching rules based on resource type, compartment or OCID
- How does the "any" keyword function when combining multiple conditions in a policy? At least one condition within the curly braces must be true for the policy to be true
- What is the primary benefit of using individual permissions instead of verbs such as "manage" in OCI policies? Enhance security by enforcing the principle of least privilege
- How does a policy reference a network source to control access? By referencing the network source name using request.networkSource.name
- Tag Based Access Control (TBAC) policies allow you to define conditions based on tags associated with: Both the requesting resource (group/compartment) and the target resource


## Networking VCN
- 


#### Skill Check
- 






















