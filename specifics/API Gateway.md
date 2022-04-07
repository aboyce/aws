## API Gateway

API Standards:

- REST (Representational State Transfer)
- SOAP (Simple Object Access Protocol)

You can define endpoints to different targets (Lambda, EC2, DynamoDB etc.), it is deeply integrated with Lambda.

Allows you to host multiple versions and stages of your APIs (development, test, production). Can create and distribute API keys to developers, and can also use AWS Signature v4 to authorise access to your APIs. Provides SDK generation for Android, IOS, and JavaScript along with support for OpenAPI standards (Swagger). Supports request/response data transformation.

Provides autoscaling but can throttle and monitor API requests to protect your back end services. API caching allows you to cache your endpoints response, reducing load on the backend.

Same Origin Policy is a security concept where a browser prevents requests from a webpage of a different origin. This prevents XSS attacks. It is enforced by the web browser but not Postman/Curl etc. CORS (Cross Origin Resource Sharing) is one way the server at the other end can relay the same-origin policy, used for fonts etc. CORS is enforced by the client.
