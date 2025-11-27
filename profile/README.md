# Repositories

## AWS Click Relay

[**AWS Click Relay**](https://github.com/TradersClub24/aws-click-relay) is a middleware service that sits between marketing emails and Keap (Infusionsoft). It forwards customers to Keap-based click targets without exposing the actual Keap tracking links in email bodies—all Keap links are replaced with **tc24content.de** links, improving email reputation and deliverability.

### Key Features

- **Click & Pixel Tracking**: Anonymized URL relay and invisible tracking pixels for email opens
- **Opt-in/Opt-out Management**: Handle email subscription preferences via Keap
- **User Management**: Process registrations and sync with AWS Cognito
- **Magic Links**: JWT-based passwordless authentication
- **Email Burst Mode**: Lambda concurrency control for high-volume campaigns

### Tech Deployment

Deployed on AWS ECS Fargate. Uses DynamoDB for link storage, S3 for images, Cognito for authentication, and integrates directly with the Keap API. Infrastructure is managed via Terraform with remote state stored in S3.

## TC24 License Service

The [**TC24 License Service**](https://github.com/TradersClub24/license-service) is a Python microservice that automates trading demo account provisioning and license management. Built with aiohttp and Python 3.12, it serves as an integration layer between TradersClub24's CRM and external trading platforms.

### Core Functionality

The service exposes a REST API that orchestrates:

- **Demo Account Creation** via the Tools4FX API (with predefined balance, leverage, and broker settings)
- **License Generation** through 4xsoft.com's licensing system
- **CRM Synchronization** to update Keap contact records with account credentials

### Deployment

Containerized with Docker and deployed to AWS ECS Fargate using Terraform. Configuration is managed through environment variables, with secrets stored in AWS Secrets Manager.

### Use Case

When a prospect requests a demo account, CRM workflows trigger this service to automatically create their trading account, generate a license, and update their contact record—eliminating manual intervention and ensuring consistent onboarding.
