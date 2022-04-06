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
