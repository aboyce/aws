## Lambda

Lambda scales out but not up automatically, you have to increase the memory.

Lambda functions can initiate other Lambdas.

Zip uploads must be no larger than 50MB compressed.

You can package code (frameworks, SDKs, libraries) as lambda layers to share across functions.

They can run up to 15 minutes.

When called through the AWS mobile SDK, lambda functions automatically gain insight into the invoking device through the 'context' object.

Can use step functions to coordinate a series of lambda functions, they maintain state for you.

### Supported languages

- Java
- Go
- PowerShell
- Node.js
- C#
- Python
- Ruby

### Version Control

Can have multiple versions of functions, the latest will be `$latest`. Qualified version will have `$latest` unqualified will not have it.

Version are immutable.

Can split traffic using aliases to different versions, but cannot split traffic with `$latest` you have to use an alias.

### Pricing

Charged on the number of requests. First million are free then $0.20 per million. Also charged on the duration, rounded to the nearest 100ms and depends on the amount of memory you allocate.

### Resources

You can set your memory in 64MB increments from 128MB to 3GB.

### Security

For sensitive information (such as passwords) it is recommended to use client side encryption using KMS ans store the ciphertext in an environment variable, this can then be decrypted in code.

### Edge

Lambda@Edge allows you to run code globally in response to CloudFront requests. Events are:

- Viewer Request
- Viewer Response
- Origin Request
- Origin Response

The main difference is the location/latency, it runs closest to the requesting user in the edge.
