## Security

### Shared Responsibility Model

#### AWS

AWS is responsible for the 'security of the cloud':

- Compute
- Storage
- Database
- Networking
- AWS Global Infrastructure
  - Regions
  - Availability Zones
  - Edge Location

#### Customer

The customer is responsible for the 'security in the cloud':

- Customer Data
- Platforms, Applications, Identity and Access Management
- Operating Systems, Network and Firewall Configuration
- Client-side Data Encryption and Data Integrity Authentication
- Server-side Encryption (File System and/or Data)
- Network Traffic Protection (Encryption, Integrity, Identity)

### AWS Virtual Private Cloud

A logically isolated section of the AWS cloud that you can launch AWS resources in a virtual network that you define. You have control of this environment, including; selection of IP address ranges, creation of subnets, and configuration of route tables and network gateways.

They support both IPv4 and IPv6.

You can provide internet facing public subnets and keep core services (like databases) in a private subnet without any internet access.

You can use Security Groups and Access Control Lists to lock down the VPC.

You can use a hardware VPN to access this virtual cloud, to use it as an extension to your on-prem data center.

### AWS KMS (Key Management Service)

Secure and resilient service that uses hardware security modules to protect your keys. Allows you to create and manage cryptographic keys and control their use across a wide range of AWS services and in applications. Is integrated with AWS CloudTrail to provide logs of all key uses for regulation and compliance.

### AWS Certificate Manager

Lets you provision, manage, and deploy public and private SSL/TLS certificate for used with AWS services and internal connected resources. Removes the time-consuming manual process of purchasing, uploading, and renewing SSL/TLS certificates.

### Protecting Data at Rest in AWS S3

AWS S3 provides server-side encryption (AES-256) using AWS maintained keys or customer provided keys. It is an optional step when you upload your data, it is on by default with AWS S3 Glacier.

- Amazon S3 Managed Keys (SSE-S3)
- AWS KMS Managed Keys (SSE-KMS)
- Custom Provided Keys (SSE-C)

Customers can also encrypt data before storage (client-side encryption).

### AWS Identity and Access Management (IAM)

#### IAM User

An IAM user with Administrator permissions is not the same as the account root user.

- Represents a person or service
- Is authenticated through credentials
  - Username and password
  - Access key and secret key

#### IAM Group

- A collection of IAM users
- Can specify permissions for multiple users
- Is easier to manage than individual user permissions

#### IAM Role

- You should prefer IAM roles over access keys
- A set of permissions that grant access to actions and resources
- Not assigned to any one person, it is assignable to anyone who needs it
- Can delegate access to IAM user, applications, and services
- Does not have standard, long term credentials, such as passwords or access tokens
- When a user assumes a role, temporary credentials are automatically created and assigned to that user
- Can be used to grant access to resources across AWS accounts
- Can be used to grant access to applications without having to embed keys into the application

#### IAM Policy

- Defines authorisation (granting permissions)
- Usually stored as JSON documents
- They are assigned to users, groups, and roles
- Policy concepts:
  - Elements such as:
    - `Effect`
    - `Action`
    - `Resource`
    - `Condition`
    - `Principle`
  - Evaluation logic such as:
    - `Explicit Deny`
    - `Explicit Allow`
    - `Implicit Deny`

### AWS Security Token Service (STS)

Provides trusted or federated users with IAM temporary credentials via IAM roles.

You get a session with is made up of:

- Access Key Id
- Secret Access Key
- Session Token
- Expiration (15 minutes to 36 hours)

### Identity Federation

Authenticate using external identities (federated users), this allows the ability to grant access to AWS without having to create IAM users. It uses AWS STS to link up the user with temporary credentials.

Could be:

- Web identity federation
  - Amazon Cognito
  - Log in with Amazon
  - Facebook
  - Google
  - OpenID Connect (OIDC)
- SAML 2.0 (Security Assertion Markup Language 2.0) based federation
  - Microsoft Active Directory
  - LDAPS
  - Open LDAP
