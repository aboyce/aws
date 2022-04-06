## Development with AWS Services

### AWS S3

A bucket is part of a global namespace that you create, the name is unique across the entire region.

An object is a file or an object that you put inside of a bucket. It is made up of a:

- Key
- Version Id
- Size

ACLs are used to grant permissions at the object or bucket level.

A bucket policy is a resource based AWS IAM access policy, you add a policy to a bucket to grant other IAM accounts or users permissions to S3 resources.

### AWS DynamoDB

A fully managed, NoSQL database service that provides fast and predictable performance with seamless scalability. Runs exclusively on SSDs.

The service stores three geographically replicas of each table to ensure high availability and durability.

When reading the data, the user can decide if they want the read to be strongly consistent or eventually consistent.
