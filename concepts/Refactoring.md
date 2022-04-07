## Refactoring

### Design Services, not Servers

- Simple applications run on persistent servers ❌
- Serverless solutions is provisioned at the time of need ✔

- Applications communicate directly with one another ❌
- Message queues handle communication between applications ✔

- Static web assets are stored locally on instances ❌
- Static web assets are stored externally, such as on S3 ✔

- Back-end servers handle user authentication and user state storage ❌
- User authentication and user state storage are handled by managed AWS services ✔

### Avoid Single Points of Failure

A common solution to a single database server, is to create a secondary server on standby. Ensure that the servers/services can swap across to the secondary without any interaction.

### Use Caching

Caching can improve performance, reduce load on the backend services, and can also reduce cost as the core services have less work to do. For example, caching files in S3 with CloudFront to distribute files.

## Migration

Migrations require both business and IT strategies.

The initial steps are:

- (1) **Discover**
- (2) **Determine**

The six R's of migration are:

- (3) **Re-host** (lift and shift)
  - Manual
    - (4) Install
    - (5) Config
    - (6) Deploy
    - (7) Validation
    - (8) Transition
    - (9) Production
  - Automate
    - (4) Use migration tools
    - (5) Validation
    - (6) Transition
    - (7) Production
- (3) **Re-platform** (lift, tinker, and shift)
  - (4) Determine platform
  - (5) Modify infrastructure
  - (6) Use migration tools
  - (7) Validation
  - (8) Transition
  - (9) Production
- (3) **Re-purchase** (drop and shop)
  - (4) Buy COTS/SaaS
  - (5) Install/setup
  - (6) Validation
  - (7) Transition
  - (8) Production
- (3) **Re-factor** (re-architecturing)
  - (4) Redesign
  - (5) App Code Development
  - (6) ALM/SDLC
  - (7) Integration
  - (8) Validation
  - (9) Transition
  - (10) Production
- (3) **Retain** (keep it as it is, not effective enough to move to the cloud)
- (3) **Retire** (eventually stop using the service, not enough benefit from migration)
