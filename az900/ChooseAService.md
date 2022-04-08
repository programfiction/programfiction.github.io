## ACS VS AKS VS WEB APP Service

##### What and How to choose between 3 Container services
| Parameters | ACI | AKS | WEB APP Service | 
   |--|--|--|--|
   | Price  | Low cost as provision without having to adopt a higher-level service.pay only for container group duration (Memory: $0.000004 per GB-s, vCPU: $0.000012 per vCPU-s) | Quick and easy deploy containerized applications without container orchestration expertise. Need to pay for VMs(virtual machines instances, storage and networking resources Kubernetes cluster) | Deploy the containerized app with your preferred dependencies to production in seconds. You need to pay only for App plan |
   | Scale  | User need configure, Scalable with container groups | Scalable solution by design, built-in application autoscaling  | Is also scalable. user need to select special App plan  |
   | Monitor and diagnostic tools | ACI provides container logs and few alert diagrams but it is not enough |  full control with VMs can remote control or use tools like Kudu to connect to monitor | few alerts and Kudu tool to analyze, can monitor App plan service |
   | Features | One public IP and dns, but ACI does not provide SSL encryption | AKS provides public IP, dns and SSL encryption. Complex configuration | Public IP, few DNS names per plan and also SSL encryption. configure using Azure portal. Recently news to use Web App service for multi containers. |
   
