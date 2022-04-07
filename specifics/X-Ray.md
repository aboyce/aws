## X-Ray

Way of diving into AWS services to find out what has happened.

Can use the X-Ray SDK to send data to it.

Will create diagrams to display progress.

The SDK provides:

- Interceptors to add to code to trance incoming HTTP requests.
- Client handlers to instrument AWS events that your app uses to call other AWS services.
- HTTP client to instrument calls to internal/external HTTP services.

### Integration

X-Ray integrates with:

- Elastic Load Balancing
- Lambda
- API Gateway
- Elastic Compute Cloud (EC2)
- EC2 Container Service (ECS)
- Elastic Beanstalk

### Languages

X-Ray supports tracing for applications that are written in:

- Node.js
- Java
- .NET
