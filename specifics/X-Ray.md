## X-Ray

Way of diving into AWS services to find out what has happened. It can be especially useful piecing together the parts and debugging a microservice architecture.

Provides an end-to-end view of your requests as they travel through your application and shows a map of your application's underlying components. The service maps can highlight bottlenecks in the design as it may become obvious which components are getting hit the hardest and by what.

Can use the X-Ray SDK to send data to it.

Will create diagrams to display progress.

### SDK

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
