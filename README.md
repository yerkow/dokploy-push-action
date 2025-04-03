# Dokploy Deployment Workflow

Welcome to the Dokploy Deployment Workflow! This repository is set up to automate the deployment of your application using GitHub Actions and Dokploy. With every push to the repository, the deployment process is triggered, making it easy to manage your application's lifecycle.

---

## 📦 **Workflow Overview**

This workflow is designed to automatically deploy your application to Dokploy when changes are pushed to your repository. The workflow includes two main steps:

1. **Checkout Code:** The latest code from the repository is checked out.
2. **Deploy Application:** The application is deployed to the Dokploy environment using the Dokploy API.

---

## 🔑 **Prerequisites**

Before you can use this workflow, you'll need to set up a few secrets in your GitHub repository:

1. **DOKPLOY_URL:** The URL of your Dokploy dashboard, where the API is accessible (without a trailing slash).
2. **DOKPLOY_APP_ID:** The ID of your application in Dokploy.
3. **DOKPLOY_AUTH_TOKEN:** Your Dokploy authentication token.

### 🛠️ How to Set Secrets:

1. Navigate to your repository's **Settings**.
2. Select **Secrets** from the sidebar.
3. Click **New repository secret**.
4. Add the following secrets:
   - `DOKPLOY_URL`
   - `DOKPLOY_APP_ID`
   - `DOKPLOY_AUTH_TOKEN`

---

## 🚀 **Quick Setup Guide**

### 1. **Clone or Fork the Repository**

To get started, either clone or fork this repository to your GitHub account.

### 2. **Configure Your Secrets**

Make sure to configure the necessary secrets in your repository as described above.

### 3. **Push Changes**

Once your secrets are set up, simply push changes to your repository, and the workflow will automatically trigger the deployment.

---

## 📝 **Workflow Configuration**

The core of the deployment process is managed in the `.github/workflows/deploy.yml` file. Here's an example configuration:

```yaml
name: Dokploy Deployment Workflow

on: [push]

jobs:
  push-dokploy:
    runs-on: ubuntu-latest
    steps:

    - name: Dokploy Application Push trigger
      uses: yerkow/dokploy-push-action@1.0.0
      with:
        DOKPLOY_URL: ${{ secrets.DOKPLOY_URL }}
        DOKPLOY_APP_ID: ${{ secrets.DOKPLOY_APP_ID }}
        DOKPLOY_AUTH_TOKEN: ${{ secrets.DOKPLOY_AUTH_TOKEN }}