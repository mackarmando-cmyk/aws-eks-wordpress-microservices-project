# Amazon EKS WordPress Microservices Architecture

## Architecture Overview

This project deploys a containerized WordPress application on Amazon EKS using Kubernetes and Helm.

Traffic Flow:

Users
↓
Internet
↓
AWS Application Load Balancer
↓
Kubernetes Service (LoadBalancer)
↓
WordPress Pods
↓
Amazon EKS Cluster
↓
EC2 Worker Nodes (3 x t3.medium)
↓
Amazon EBS Persistent Storage

Auto Scaling:

Horizontal Pod Autoscaler (HPA)
↓
Monitors CPU Utilization
↓
Automatically Scales Pods

Future Enhancements:

- AWS WAF
- AWS Certificate Manager
- Amazon S3 Backups
- AWS Secrets Manager
- Private Worker Nodes
- HIPAA-aligned Architecture
