# Networking Design

## VPC
- CIDR: 10.0.0.0/16
- DNS resolution and hostnames enabled
### Resource Map for Reference:
<img width="1646" height="462" alt="image" src="https://github.com/user-attachments/assets/fe8d9a65-f205-48e7-ae0f-109dbc32e73c" />

## Subnets
### Public Subnets
- Used for Application Load Balancer and NAT instance
  - Ideally, a NAT Gateway should be deployed here to allow private subnets to access the internet with higher availability, minimal overhead, and better security.
  - This project utilizes a NAT instance for cost savings and `iptables` configuration practice.
- Internet Gateway attached
- Public 1:
  - AZ: us-east-1a
  - CIDR: 10.0.0.0/24
- Public 2:
  - AZ: us-east-1b
  - CIDR: 10.0.1.0/24

### Private Application Subnets
- Host ECS container instances and tasks
- No public IP assignment
- Default route points to a self-managed NAT instance
- Private 1:
  - AZ: us-east-1a
  - CIDR: 10.0.10.0/24
- Private 2:
  - AZ: us-east-1b
  - CIDR: 10.0.11.0/24

## Routing
- Public subnets route 0.0.0.0/0 to Internet Gateway
- Private subnets route 0.0.0.0/0 to NAT instance

This design ensures application workloads are not directly reachable from the internet while still supporting controlled outbound connectivity.
