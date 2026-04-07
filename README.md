# Symplichain System Design Assignment

This repository contains the CI/CD workflow configuration for deploying the Symplichain platform.

## Overview

The pipeline is triggered on code pushes:
- `staging` branch → deploys to staging environment
- `main` branch → deploys to production environment

## Workflow Steps

- Checkout code
- Build React frontend
- Upload static files to S3
- SSH into EC2 instance
- Pull latest backend code
- Run database migrations
- Restart Gunicorn and Celery services

## Notes

This is a conceptual implementation aligned with the given architecture using Django, React, AWS EC2, and S3.
