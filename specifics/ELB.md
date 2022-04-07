## Elastic Load Balancer (ELB)

Automatically distributes incoming application traffic across multiple targets and virtual appliances in one or more availability zones.

If you get a 504 it means the gateway has timed out, troubleshoot the application.

### Application Load Balancer

- Layer 7
- Target type: IP, Instance, Lambda
- Can make clever routing decisions

### Network Load Balancer

- Layer 4
- Target type: IP, Instance, Application Load Balancer
- Super fast, high performance
- Most expensive

### Gateway Load Balancer

- Layer 3 Gateway and Layer 4 Load Balancing
- Target type: IP, Instance

### Classic Load Balancer

- Deprecated
- Layer 7 or layer 4, but a lot less layer 7 features
- `X-Forwarded-For` header will contain the public IP address
