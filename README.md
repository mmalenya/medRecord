# MedRecord

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)](https://github.com)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Java](https://img.shields.io/badge/Java-21-orange.svg)](https://openjdk.org/)
[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/)

## Description

MedRecord is a multi-tenant patient records management platform designed for healthcare providers. It provides secure, scalable, and compliant electronic health record (EHR) management with tenant isolation, audit logging, and real-time notifications.

## Architecture Overview

MedRecord uses a microservices architecture deployed on AWS infrastructure with the following key components:

- **Microservices Layer**: Spring Boot services for core business logic
- **Serverless Layer**: AWS Lambda functions for event-driven processing
- **Data Layer**: Amazon RDS (PostgreSQL) with Row-Level Security (RLS)
- **Messaging Layer**: Amazon MSK (Managed Kafka) for event streaming
- **Container Orchestration**: Amazon EKS for service deployment

```
[Architecture Diagram Placeholder]
```

## Technology Stack

### Backend Services
- **Java 21** - Spring Boot microservices
- **Python 3.11** - AWS Lambda functions
- **Spring Security** - Authentication & Authorization
- **Spring Data JPA** - Data access layer

### Infrastructure
- **AWS EKS** - Kubernetes orchestration
- **Amazon RDS** - PostgreSQL database
- **Amazon MSK** - Kafka message broker
- **AWS Lambda** - Serverless functions
- **Amazon ECR** - Container registry

### DevOps
- **Docker** - Containerization
- **Terraform** - Infrastructure as Code
- **Helm** - Kubernetes package management
- **GitHub Actions** - CI/CD pipelines

## Project Structure

```
medRecord/
├── services/              # Spring Boot microservices
│   ├── auth-service/      # Authentication & authorization
│   ├── patient-service/   # Patient records management
│   ├── tenant-service/    # Multi-tenant provisioning
│   └── audit-service/     # Audit logging
├── lambda/                # AWS Lambda functions
│   ├── tenant-provisioner/       # New tenant setup
│   ├── rls-policy-manager/       # Database security policies
│   ├── audit-archiver/           # Archive old audit logs
│   └── notification-dispatcher/  # Send notifications
├── terraform/             # Infrastructure as Code
│   ├── modules/           # Reusable Terraform modules
│   └── environments/      # Environment-specific configs
├── k8s/                   # Kubernetes manifests
├── helm/                  # Helm charts
├── .github/               # GitHub Actions workflows
├── docs/                  # Project documentation
└── scripts/               # Utility scripts
```

## Getting Started

### Prerequisites

- **Java 21** - [Download](https://openjdk.org/)
- **Maven 3.9+** - [Download](https://maven.apache.org/)
- **Docker Desktop** - [Download](https://www.docker.com/products/docker-desktop)
- **AWS CLI** - [Download](https://aws.amazon.com/cli/)
- **Terraform 1.5+** - [Download](https://www.terraform.io/downloads)
- **kubectl** - [Download](https://kubernetes.io/docs/tasks/tools/)
- **Helm 3** - [Download](https://helm.sh/docs/intro/install/)

### Local Development Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/medRecord.git
   cd medRecord
   ```

2. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. **Start local dependencies**
   ```bash
   docker-compose up -d
   ```

4. **Build services**
   ```bash
   # Build all Java services
   cd services/auth-service && mvn clean install
   cd ../patient-service && mvn clean install
   cd ../tenant-service && mvn clean install
   cd ../audit-service && mvn clean install
   ```

5. **Run services locally**
   ```bash
   # Each service can be run with:
   cd services/<service-name>
   mvn spring-boot:run
   ```

### Running Tests

```bash
# Run unit tests for all services
mvn test

# Run integration tests
mvn verify

# Run Lambda function tests
cd lambda/<function-name>
pytest tests/
```

## Deployment

For detailed deployment instructions, see:
- [Infrastructure Setup](docs/deployment/infrastructure-setup.md)
- [Service Deployment](docs/deployment/service-deployment.md)
- [Environment Configuration](docs/deployment/environment-config.md)

Quick deployment overview:
1. Provision infrastructure with Terraform
2. Build and push Docker images to ECR
3. Deploy services to EKS using Helm
4. Deploy Lambda functions with Terraform

## Contributing

We welcome contributions! Please read our [Contributing Guidelines](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions or support, please open an issue on GitHub or contact the development team.
