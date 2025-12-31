# Amazon ECS (EC2 Launch Type)

## ECS Cluster
- ECS cluster using EC2 launch type
- ECS-optimized Amazon Linux 2 AMI

## Container Instances
- Deployed in private subnets
- No public IP addresses
- Registered to ECS cluster via user data configuration
- Managed via Systems Manager (SSM)
### Screenshot
<img width="1873" height="603" alt="image" src="https://github.com/user-attachments/assets/9334e066-0113-44d8-abf7-117409876388" />

## Task Definition
- Network mode: `awsvpc`
- Application container: OWASP Juice Shop Pulled from Private ECR Repository
- Port: 3000
- CloudWatch Logs enabled
### Screenshot
<img width="1587" height="496" alt="image" src="https://github.com/user-attachments/assets/90c18686-8d1a-45d3-9219-a34810d558d2" />

## Service
- Desired count: 1
- Integrated with Application Load Balancer
### Screenshot
<img width="1598" height="316" alt="image" src="https://github.com/user-attachments/assets/ddf8cd10-d6fc-4f1f-97f7-278bbbeafb3e" />

