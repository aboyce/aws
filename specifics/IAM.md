## Identity and Access Management (IAM)

What does it provide?

- Centralised control of AWS accounts
- Shared access to accounts
- Granular permissions
- Identify federation (AD, Facebook, LinkedIn, etc.)
- Multi-factor authentication
- Temporary access to users/devices and services (mobile apps etc.)
- Password retention policy

It is global, i.e. it does not apply to a specific region.

New users have no permissions when they are created, root has all.

#### IAM Policy

A policy is a document that defines one or more permissions, can be applied to a user, group, or a role.

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

### Inline vs. Managed vs. Custom Policies

#### Inline

Embedded within the user, group, role which it applied to. String 1:1 relationship between the entity and the policy. In most cases is not used.

#### Managed

Created and administered by AWS. Created for common cases. Cannot change them yourself.

#### Custom (Customer)

Created and administered inside your account. Created by you for your specific needs, but you can just copy a managed one.

### Web Identify Federation

Authenticate using external identities (federated users), this allows the ability to grant access to AWS without having to create IAM users. It uses AWS STS to link up the user with temporary credentials that map to an IAM role.

Providers:

- Amazon Cognito
- Log in with Amazon
- Facebook
- Google
- OpenID Connect (OIDC)

#### Cognito

Provides web identity federation and:

- Sign in/up to you application
- Guest user accounts
- Act as an identity broker
- Synchronises data between devices
- Recommended for all mobile AWS

##### User Pools

User directories to manage sign in/up functionality for web and mobile applications. Users can sign in directly or indirectly using an identity provider. Successful authentication generates a number of JWTs.

##### Identity Pools

Enables the creation of unique identities for users and authenticate them with identity providers. This allows them to use AWS services. Cognito uses push synchronisation (using SNS) to update (silently) that the user data has changed.
