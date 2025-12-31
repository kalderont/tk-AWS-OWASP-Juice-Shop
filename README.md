# AWS Cloud Security Project – OWASP Juice Shop - Tal Kalderon

This project demonstrates the design and deployment of a secure AWS cloud environment hosting the OWASP Juice Shop application. 
The environment is intentionally built in stages to validate security controls through attack simulation and observable evidence.

## Project Phases
1. **Baseline Infrastructure (Current State)**
   - ECS-based application deployment without WAF
   - Private subnets with controlled egress
   - TLS-enabled public ingress
2. Attack Simulation with Burp Suite
   - Path Traversal (OWASP 1: Broken Access Control)
   - SQL Injection (OWASP 5: Injection)
   - XSS Exploitation (OWASP 5: Injection)
4. Web Application Firewall (WAF) Integration
   - Attachment of WAF to ALB
   - Custom and Managed Rule Configuration
   - Enable Logging
6. Post-WAF Attack Validation and Log Analysis
   - Exploitation Reattempt
   - Blocked Request Validation
   - CloudWatch Logs Analysis

## High-Level Goals
- Host a deliberately vulnerable application in AWS
- Isolate workloads from direct internet exposure
- Enforce encrypted ingress
- Establish observability prior to adding advanced controls
- Demonstrate measurable security improvement after mitigation

## Application
- OWASP Juice Shop (containerized - Docker)

