# Architecture Overview 

Stage 1: (Baseline – No WAF)

The baseline architecture hosts the OWASP Juice Shop application using Amazon ECS on EC2 instances within private subnets. The application is exposed to the internet exclusively through an Application Load Balancer (ALB).

### Design Principles
- No public IPs on application compute
- Centralized ingress via ALB
- Encrypted client-to-load-balancer communication
- Controlled outbound internet access via a self-managed NAT instance
- Administrative access without inbound SSH

### Traffic Flow
1. Users access the application via HTTPS (443) on the ALB
2. ALB forwards traffic to ECS tasks in private subnets
3. ECS tasks communicate outbound via a NAT instance for required egress
4. Administrators access EC2 hosts via AWS Systems Manager (SSM)

### Current State
At this stage, no Web Application Firewall (WAF) rules are applied. This provides a baseline for observing attack behavior and application responses prior to mitigation.

Stage 2: (Secured - WAF Enabled)
