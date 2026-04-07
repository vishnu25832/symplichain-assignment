# Symplichain System Design Assignment

This repository contains a conceptual CI/CD workflow and system design approach for the Symplichain platform.

## Overview

The system is designed to handle multiple customers accessing a shared external API with strict rate limits. The goal is to ensure controlled request flow, fairness, and reliability under load.

## Key Design Highlights

### Request Handling
- Queue-based architecture using Redis and Celery
- Separate queues per customer
- Round-robin scheduling for fairness

### Rate Limiting
- Enforced at 3 requests per second
- Implemented using Celery rate limiting or Token Bucket

### Failure Handling
- Exponential backoff for retries
- Retry limits to prevent overload

### CI/CD Pipeline
The deployment pipeline is triggered on:
- `staging` branch → deploy to staging
- `main` branch → deploy to production

#### Steps
- Checkout code
- Build frontend (conceptual)
- Upload static files to S3
- Deploy backend to EC2
- Run migrations
- Restart services (Gunicorn, Celery)

### Debugging Approach
- Step-by-step tracing along data flow:
  Driver App → Django → S3 → Celery → Bedrock → RDS
- Log-based debugging using system tools

## Tech Stack

- Backend: Django, Celery, Redis
- Frontend: React
- Infrastructure: AWS EC2, S3, RDS
- CI/CD: GitHub Actions

## Note

This implementation is conceptual and focuses on system design thinking rather than production deployment.

## Author

Vishnu Vardhan B
