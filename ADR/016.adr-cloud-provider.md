# Cloud provider
Date: 2024.09.28

## Status
Accepted

## Context

The Clearview Platform, being developed by an NGO, needs a cost-effective cloud provider with the following requirements:

- API Gateway
- Object Storage with Cold Storage Options
- Managed PostgreSQL
- Low-Cost Serverless Functions (Pay-per-request)
- Logging
- Sidecar Architecture
- CI/CD Pipeline
- Cost efficiency due to NGO funding constraints
- Other Non functional requirements of the system


## Decision

| Criteria                      | AWS                                           | GCP                                           | Azure                                      |
|-------------------------------|-----------------------------------------------|----------------------------------------------|--------------------------------------------|
| Cost Efficiency               | Competitive pricing, NGO credits.             | Competitive pricing, NGO credits.            | Similar pricing, NGO credits.              |
| Logging                       | CloudWatch (integrated logging).              | Google Cloud Logging (Operations suite).    | Azure Monitor/Log Analytics.               |
| Sidecar Architecture          | ECS/EKS with App Mesh.                        | GKE with Istio support.                      | AKS with Service Mesh.                     |
| CI/CD Pipeline                | CodePipeline.                                 | Cloud Build (managed CI/CD).                 | Azure DevOps, GitHub Actions.              |
| Serverless Functions          | AWS Lambda (pay-per-request).                 | Cloud Run/Cloud Functions (pay-per-request). | Azure Functions (pay-per-execution).       |
| Object Storage (Cold Storage) | S3 Glacier (affordable cold storage).         | Coldline Storage (low-cost cold storage).    | Blob Archive Storage (cold storage).       |
| Managed PostgreSQL            | RDS for PostgreSQL.                           | Cloud SQL for PostgreSQL.                    | Azure Database for PostgreSQL.             |
| API Gateway                   | AWS API Gateway (pay-per-request).            | GCP API Gateway (pay-per-request).           | Azure API Management (various tiers).      |
| NGO Support                   | Extensive credits and support.                | Strong credits and support.                  | Similar credits and support.               |
| AI/ML Future Needs            | Amazon SageMaker (for ML).                    | GCP AI/ML tools (stronger integration for future AI). | Azure AI and Cognitive Services.          |


We have chosen Google Cloud Platform (GCP) as the cloud provider for the Clearview Platform for the following reasons

- Cost Efficiency: GCP offers competitive pay-per-request pricing with substantial NGO credits. Given the cost constraints of the platform, this aligns well with our financial needs.

- Logging and Monitoring: Google Cloud Logging is well-integrated across all GCP services, providing real-time, centralized monitoring and insights, which will support our operational observability needs.

- Sidecar Architecture: GKE (Google Kubernetes Engine) supports sidecar containers with seamless integration, allowing us to easily manage microservices patterns and ensure observability, security.

- CI/CD Pipeline: Cloud Build offers a managed CI/CD pipeline, with strong integration into GCP services. This aligns with our need for streamlined deployment processes, and supports automation with minimal overhead.

- Object Storage: Coldline Storage provides low-cost, long-term storage for resumes, particularly anonymized or archived versions, which is crucial for our platform's storage requirements.

- Managed PostgreSQL: Cloud SQL for PostgreSQL meets the need for a fully managed relational database, ensuring high availability and scalability.

- AI/ML Future Needs: As the platform may eventually incorporate AI features like resume anonymization and recommendation engines, GCP’s AI/ML suite is the strongest option for future-proofing, offering robust integrations with document analysis tools.


## References

- GCP Documentation
- AWS Documentation
- Azure Documentation
