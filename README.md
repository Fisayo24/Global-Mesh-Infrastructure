# Global-Mesh-Infrastructure: Multi-Region AWS Deployment

## Executive Summary
This repository contains a production-ready Terraform configuration that automates the deployment of a cross-continental AWS infrastructure. By leveraging **Terraform Modules** and **Provider Aliasing**, this project provisions identical, isolated networking environments in both `us-east-1` (N. Virginia) and `eu-west-1` (Ireland) from a single source of truth.

### Key Engineering Highlights
* **Dry Architecture:** Developed a reusable VPC module to ensure consistency across regions while reducing code duplication.
* **Multi-Region Orchestration:** Utilized provider aliases to manage resources across multiple AWS geographic locations.
* **State Persistence & Locking:** Configured a remote S3 backend with DynamoDB locking to enable team collaboration.
## 🌐 Phase 1: Global Networking Foundation
The first stage of the deployment focuses on establishing a consistent networking footprint across **US-East-1** and **EU-West-1**. Using a single reusable VPC module, I orchestrated the simultaneous creation of isolated environments.

### 📊 Networking Validation
The output below confirms the successful planning of 8 core networking resources (VPCs, Public Subnets, and IGWs):

(./infra-validation-8<img width="960" height="504" alt="infra-validation-8-resources" src="https://github.com/user-attachments/assets/06b1ad91-afbf-4fa7-8f4e-4328a1cc51b4" />
-resource.png)
