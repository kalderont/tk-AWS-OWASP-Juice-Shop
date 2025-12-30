# AWS Cloud Security Project – OWASP Juice Shop - Tal Kalderon

This project demonstrates the design and deployment of a secure AWS cloud environment hosting the OWASP Juice Shop application. 
The environment is intentionally built in stages to validate security controls through attack simulation and observable evidence.

## Project Phases
1. **Baseline Infrastructure (Current State)**
   - ECS-based application deployment without WAF
   - Private subnets with controlled egress
   - TLS-enabled public ingress
2. Attack Simulation (OWASP Top 10)
3. Web Application Firewall (WAF) Integration
4. Post-WAF Attack Validation and Log Analysis

This repository documents **Phase 1: Baseline Infrastructure**.

## High-Level Goals
- Host a deliberately vulnerable application in AWS
- Isolate workloads from direct internet exposure
- Enforce encrypted ingress
- Establish observability prior to adding advanced controls
- Demonstrate measurable security improvement after mitigation

## Application
- OWASP Juice Shop (containerized)

