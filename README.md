# aws-eks-wordpress-microservices-project

Designed and deployed a cloud-native WordPress application on Amazon EKS with Kubernetes orchestration, Helm package management, LoadBalancer services, and Horizontal Pod Autoscaling.

This project demonstrates deployment of a containerized WordPress application on Amazon Elastic Kubernetes Service (EKS).

**Technologies Used**:
- AWS EKS
- Kubernetes
- Helm
- WordPress
- LoadBalancer Services
- Horizontal Pod Autoscaler (HPA)

## Horizontal Pod Autoscaling

Implemented a Kubernetes Horizontal Pod Autoscaler (HPA) to dynamically scale application pods based on CPU utilization.

Configuration:

- Minimum Replicas: 1
- Maximum Replicas: 5
- CPU Threshold: 50%

**Benefits**:

- Automatic scaling during traffic spikes
- Improved application availability
- Better resource utilization
- Reduced operational overhead

**Business Problem**

Traditional monolithic applications are difficult to scale and manage.
This project demonstrates how Kubernetes and Amazon EKS can be used to deploy, manage, and automatically scale containerized workloads.

**Architecture**
User
 ↓
AWS Load Balancer
 ↓
Kubernetes Service
 ↓
WordPress Pods
 ↓
Amazon EKS Worker Nodes
 ↓
AWS Infrastructure

**Skills Demonstrated**
- Amazon EKS
- Kubernetes Administration
- Helm Package Management
- Microservices Deployment
- Load Balancing
- Horizontal Pod Autoscaling
- AWS Networking
- Infrastructure Management

**Future Enhancements**

- HTTPS via AWS ACM
- AWS WAF protection
- Private EKS Nodes
- EBS encrypted storage
- Secrets Manager integration
- IAM Roles for Service Accounts (IRSA)
- HIPAA-aligned architecture
- Monitoring with Prometheus & Grafana

**Database Improvements**

- Deploy MySQL as a Kubernetes StatefulSet
- Replace self-managed database with Amazon RDS MySQL
- Store credentials using Kubernetes Secrets
- Enable automated database backups
- Configure Multi-AZ failover for high availability

### Kubernetes Validation

- Successfully deployed WordPress to Amazon EKS
- Provisioned 3 worker nodes
- Exposed application through AWS LoadBalancer
- Managed deployment using Helm charts
- Configured Metrics Server
- Implemented Horizontal Pod Autoscaler
- Verified autoscaler monitoring cluster CPU metrics
- Executed load testing validation
