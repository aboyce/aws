## API Gateway

API Standards:

- REST (Representational State Transfer)
- SOAP (Simple Object Access Protocol)

You can define endpoints to different targets (Lambda, EC2, DynamoDB etc.).

Provides autoscaling.

Can throttle API requests.

API caching allows you to cache your endpoints response.

Same Origin Policy is a security concept where a browser prevents requests from a webpage of a different origin. This prevents XSS attacks. It is enforced by the web browser but not Postman/Curl etc. CORS (Cross Origin Resource Sharing) is one way the server at the other end can relay the same-origin policy, used for fonts etc. CORS is enforced by the client.
