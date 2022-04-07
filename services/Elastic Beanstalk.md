Elastic Beanstalk## Elastic Beanstalk

Allows you to deploy your application without worrying about the infrastructure or underlying technologies. Targeted at full stack environments for web and worker tiers. Simple to use but less fine grained control. Can provide dev, test environments, or full production environments with load balancing and scaling.

Can select the EC2 instance that is most suitable for your application. Can retain full administrative control over the resource managing/running of the application. Manages updates to the infrastructure.

Monitor and manage the application health via a dashboard. Integrated with Cloudwatch and X-Ray for performance data and metrics.

### Deployment Polices

Supported options are:

#### All at once

Goes to new versions simultaneously. All instances out of service during the deployment so you will experience an outage. If it fails, you re-deploy the previous version.

#### Rolling

Deploys in batches, each batch is out of service during the deployment so the capacity will be reduced. May not be suitable if performance is key. If it fails, you have to do a rolling update to the old version.

#### Rolling with additional batch

Exactly the same as Rolling but additional resources are used to prevent the drop in capacity.

#### Immutable

Deploys new versions to a fresh group in a separate auto-scaling group. When the new batch passes health checks, they are moved to the existing auto-scaling group and the old instances are terminated.

Maintains full capacity.

If it fails, the new batch is just terminated.

### Supported languages

- Java
- .NET
- PHP
- Node.js
- Python
- Ruby
- Go
- Docker

### Supported servers

- Apache
- Nginx
- Passenger
- IIS

### Configuration

You can customise the environment using configuration files. This includes:

- Packages to install
- Linux users/groups
- Shell commands
- Specify services
- Configuration of load balancers

Written in YAML or JSON, it can be called anything but must be a `*.config`.

Extensions must be saved in a folder called `.ebextensions`.

### Integration with RDS

There are two ways of integrating RDS and Elastic Beanstalk. You can launch the instance from within the Elastic Beanstalk console, this is a good option for dev or test. This does mean the lifecycle of your database is tied to the lifecycle of the app environment, so if you terminate it, you will lose the database. For production, you should use a separate RDS, this requires permissions.
