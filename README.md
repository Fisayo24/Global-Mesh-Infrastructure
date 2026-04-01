# Global-Mesh-Infrastructure: Multi-Region AWS Deployment

## Executive Summary
This repository contains a production-ready Terraform configuration that automates the deployment of a cross-continental AWS infrastructure. By leveraging **Terraform Modules** and **Provider Aliasing**, this project provisions identical, isolated networking environments in both `us-east-1` (N. Virginia) and `eu-west-1` (Ireland) from a single source of truth.

### Key Engineering Highlights
* **Dry Architecture:** Developed a reusable VPC module to ensure consistency across regions while reducing code duplication.
* **Multi-Region Orchestration:** Utilized provider aliases to manage resources across multiple AWS geographic locations.
* **State Persistence & Locking:** Configured a remote S3 backend with DynamoDB locking to enable team collaboration.
