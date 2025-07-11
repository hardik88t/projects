# Google Cloud Platform Deployment Guide

## Project Overview
**Replace this section with your project's GCP deployment information**

- **Project Name**: [Your GCP Project Name]
- **Project Type**: [WEBAPP/API/STATIC/etc.]
- **Primary Service**: [Cloud Run/App Engine/Compute Engine/etc.]
- **Database**: [Cloud SQL/Firestore/etc.]
- **Domain**: [Your custom domain if applicable]

## Prerequisites

### Required Tools
- [ ] Google Cloud CLI (`gcloud`) installed and configured
- [ ] Docker installed (for containerized deployments)
- [ ] Project dependencies installed locally
- [ ] GCP Project created with billing enabled

### Required APIs
Enable these APIs in your GCP project:
- [ ] Cloud Run API (for containerized apps)
- [ ] Cloud Build API (for CI/CD)
- [ ] Cloud SQL API (if using Cloud SQL)
- [ ] Cloud Storage API (for file storage)
- [ ] Cloud DNS API (for custom domains)

```bash
# Enable required APIs
gcloud services enable run.googleapis.com
gcloud services enable cloudbuild.googleapis.com
gcloud services enable sqladmin.googleapis.com
gcloud services enable storage.googleapis.com
gcloud services enable dns.googleapis.com
```

## Environment Setup

### 1. GCP Project Configuration
```bash
# Set your project ID
export PROJECT_ID="your-project-id"
gcloud config set project $PROJECT_ID

# Set default region
export REGION="us-central1"
gcloud config set run/region $REGION
```

### 2. Environment Variables
Create a `.env.production` file with your production environment variables:

```bash
# Database
DATABASE_URL="your-production-database-url"

# Project Manager Integration
PROJECT_MANAGER_DB="your-hosted-project-manager-db-url"
PROJECT_NAME="your-project-name"

# Application
NODE_ENV="production"
PORT=8080

# Add your project-specific variables
API_KEY="your-api-key"
SECRET_KEY="your-secret-key"
```

## Database Setup

### Option 1: Cloud SQL (PostgreSQL)
```bash
# Create Cloud SQL instance
gcloud sql instances create your-db-instance \
    --database-version=POSTGRES_14 \
    --tier=db-f1-micro \
    --region=$REGION

# Create database
gcloud sql databases create your-database \
    --instance=your-db-instance

# Create user
gcloud sql users create your-user \
    --instance=your-db-instance \
    --password=your-secure-password
```

### Option 2: Cloud SQL (MySQL)
```bash
# Create MySQL instance
gcloud sql instances create your-db-instance \
    --database-version=MYSQL_8_0 \
    --tier=db-f1-micro \
    --region=$REGION
```

### Option 3: Firestore (NoSQL)
```bash
# Enable Firestore
gcloud firestore databases create --region=$REGION
```

## Deployment Options

### Option 1: Cloud Run (Recommended for most apps)

#### 1. Create Dockerfile
```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci --only=production

COPY . .
RUN npm run build

EXPOSE 8080

CMD ["npm", "start"]
```

#### 2. Deploy to Cloud Run
```bash
# Build and deploy
gcloud run deploy your-service-name \
    --source . \
    --platform managed \
    --region $REGION \
    --allow-unauthenticated \
    --set-env-vars NODE_ENV=production,PROJECT_NAME=your-project-name
```

### Option 2: App Engine
```yaml
# app.yaml
runtime: nodejs18

env_variables:
  NODE_ENV: production
  PROJECT_NAME: your-project-name
  DATABASE_URL: your-database-url

automatic_scaling:
  min_instances: 0
  max_instances: 10
```

```bash
# Deploy to App Engine
gcloud app deploy
```

### Option 3: Compute Engine (For complex applications)
```bash
# Create VM instance
gcloud compute instances create your-vm-name \
    --image-family=ubuntu-2004-lts \
    --image-project=ubuntu-os-cloud \
    --machine-type=e2-micro \
    --zone=us-central1-a
```

## CI/CD Setup

### GitHub Actions with GCP
Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GCP

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3

    - name: Setup Cloud SDK
      uses: google-github-actions/setup-gcloud@v1
      with:
        project_id: ${{ secrets.GCP_PROJECT_ID }}
        service_account_key: ${{ secrets.GCP_SA_KEY }}
        export_default_credentials: true

    - name: Deploy to Cloud Run
      run: |
        gcloud run deploy your-service-name \
          --source . \
          --platform managed \
          --region us-central1 \
          --allow-unauthenticated
```

---

**Template Instructions:**
1. Replace all placeholder values with your actual project information
2. Remove sections that don't apply to your project type
3. Add project-specific configurations and requirements
4. Update this document as your deployment evolves
5. Test all commands in a development environment first
6. Keep sensitive information in environment variables or Secret Manager
