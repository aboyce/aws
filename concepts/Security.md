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

See Encryption in [S3](/specifics/S3.md)

### AWS Identity and Access Management (IAM)

See [IAM](/specifics/IAM.md)

### AWS Security Token Service (STS)

Provides trusted or federated users with IAM temporary credentials via IAM roles.

You get a session, which is made up of:

- Access Key Id
- Secret Access Key
- Session Token
- Expiration (15 minutes to 36 hours)

### Identity Federation and Web Identity Federation

See [IAM](/specifics/IAM.md)

#### SAML 2.0 (Security Assertion Markup Language 2.0) based federation

- Microsoft Active Directory
- LDAPS
- Open LDAP
