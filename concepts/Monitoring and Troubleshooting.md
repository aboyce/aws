## Monitoring and Troubleshooting

Check the AWS error code returned from operations:

- 400 series, handle the error in application
- 500 series, retry operation

Collection and analysis of log data from instances, such as:

- System logs
- HTTP logs

Monitoring of:

- Instance health and performance
- Availability of managed service (such as Amazon RDS)
- Network performance
- Utilisation for cost efficiency
- Unused or under-used instances running

Always check security groups and network access control list when troubleshooting.

Instances launched into a private subnet in a VPC cannot properly communicate with the internet unless you use NAT.

You need an IGW and a route in the route table to talk to the internet.

EBS volumes are loosely coupled to EC2 instances, can attach/detach except for the boot volume.

### CloudTrail

You can store logs on API usage in an S3 bucket and then later analyse those logs.

From this you can answer questions such as:

- Who shut down a specific instance?
- Who changed a security group configuration?
- Is any activity coming from an unknown IP address?
- What activities where denied due to lack of permissions?
