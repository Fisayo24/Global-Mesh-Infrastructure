# Global-Mesh-Infrastructure: Multi-Region AWS Deployment

## Executive Summary
This repository contains a production-ready Terraform configuration that automates the deployment of a cross-continental AWS infrastructure. By leveraging **Terraform Modules** and **Provider Aliasing**, this project provisions identical, isolated networking environments in both `us-east-1` (N. Virginia) and `eu-west-1` (Ireland) from a single source of truth.

### Key Engineering Highlights
* **Dry Architecture:** Developed a reusable VPC module to ensure consistency across regions while reducing code duplication.
* **Multi-Region Orchestration:** Utilized provider aliases to manage resources across multiple AWS geographic locations.
* **State Persistence & Locking:** Configured a remote S3 backend with DynamoDB locking to enable team collaboration.
## Phase 1: Global Networking Foundation
The first stage of the deployment focuses on establishing a consistent networking footprint across **US-East-1** and **EU-

West-1**. Using a single reusable VPC module, I orchestrated the simultaneous creation of isolated environments.

### Networking Validation
The output below confirms the successful planning of 8 core networking resources (VPCs, Public Subnets, and IGWs):

(./infra-validation-8<img width="960" height="504" alt="infra-validation-8-resources" src="https://github.com/user-attachments/assets/06b1ad91-afbf-4fa7-8f4e-4328a1cc51b4" />
-resource.png)

## Phase 2: Multi-Region Compute Deployment
With the global networking foundation validated, I utilized **output variables** to pass VPC and Subnet data into the compute layer. This ensures that EC2 instances are dynamically placed within the correct regional subnets.

### Compute Validation (Plan: 2)
The validation below confirms the simultaneous provisioning of two T2-Micro instances—one in **US-East-1** and one in **EU-West-1**:

**Validation Output:**
(./02-dynamodb-state<img width="960" height="504" alt="02-dynamodb-state-lock-active" src="https://github.com/user-attachments/assets/640b3529-dd9f-40e7-afcc-3ebe35583876" />
-lock-active.png)

### Automation Highlights
* **Dynamic Subnet Mapping:** Instances automatically inherit the CIDR and Gateway settings from the Networking module.
* **Region-Specific Providers:** Demonstrated the ability to manage compute resources across different geographic regions in a single execution plan.

* ## Phase 3: Global Compute Execution (Plan: 2)
The final stage of the deployment validates the successful provisioning of compute resources into the previously established networking mesh.

### Execution Validation Summary
The output below confirms that Terraform has successfully planned the deployment of two **T2-Micro** instances. By leveraging the modular outputs from Phase 1, these instances are automatically assigned to the correct regional subnets in **US-East-1** and **EU-West-1**.

**Final Plan Output:**
<img width="960" height="504" alt="04-compute-plan-final" src="https://github.com/user-attachments/assets/3baf7aca-777b-4543-9e79-7af35217d29b" />
(./04-compute-plan-final.png)

### Project Takeaways
* **Modular Orchestration:** Proved the ability to manage a global footprint from a single centralized configuration.
* **Security & Reliability:** Integrated S3 and DynamoDB for production-grade state management.
* **Infrastructure as Code:** Demonstrated advanced Terraform skills including provider aliasing, modules, and variable-driven logic.
