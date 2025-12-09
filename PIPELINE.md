# Deployment-Pipeline (GitHub Actions)

This document describes the deployment pipeline defined in .github/workflows/deployment.yaml.
The pipeline automates the building, publishing, and deployment of backend and frontend images, as well as updating the deployment on the server.

---

## Übersicht

This document describes the deployment pipeline defined in .github/workflows/deployment.yaml.
The pipeline automates the building, publishing, and deployment of backend and frontend images, as well as updating the deployment on the server.


1. Retrieve repository code
2. Log in to GitHub Container Registry (GHCR)
3. Build and push the backend Docker image
4. Build and push the frontend Docker image
5. Generate the `.env` file from the secret
6. Copy `docker-compose.yml` and `.env` to the server via SCP
7. Update the deployment via SSH

---
## Job Deploy

```bash
runs-on: ubuntu-latest
```

## Code Checkout

```bash
uses: actions/checkout@v6
```

## Login to GHCR

```bash
ghcr.io/flyingchris1/conduit-backend:latest
```

## Build and push backend image

```bash
ghcr.io/flyingchris1/conduit-backend:latest
```

## Build and push frontend image

```bash
ghcr.io/flyingchris1/conduit-frontend:latest
```

## Create .env file

```bash
echo "${{ secrets.ENV_FILE }}" > .env
```

## Transfer deplyment files on server

```bash
uses: appleboy/scp-action@v1
```

## Deployment via SSH

```bash
 name: Deploy on Server via SSH
        uses: appleboy/ssh-action@v1.2.4
        with:
          host: ${{ secrets.HOST }}
          username: ${{ secrets.USERNAME }}
          key: ${{ secrets.KEY }}
          port: ${{ secrets.PORT }}
```

## Trigger

```yaml
on:
  push:
    branches:
      - feature
