# my-java-docker-app

Ready-to-run sample project: Java (Spring Boot) + Docker + Azure (ACR + App Service) + Bicep + GitHub Actions.

## What it contains
- Sample Spring Boot app (hello endpoint)
- Dockerfile
- Bicep infra: creates resource group, ACR, App Service Plan, App Service
- GitHub Actions:
  - `deploy-infra.yml` (deploy infra from `infra/` on `develop`/`main` branches or manual)
  - `deploy-app.yml` (build, Dockerize, push to ACR, deploy to App Service on branch pushes)

## IMPORTANT - Before using
1. Replace placeholder values and add GitHub Secrets in repository:
   - `AZURE_CREDENTIALS` : output of `az ad sp create-for-rbac --name "github-actions" --role contributor --scopes /subscriptions/<SUB_ID> --sdk-auth`
   - `AZURE_SUBSCRIPTION_ID` : your subscription id

2. Default region in templates is **eastus**. Change if needed.

3. Default resource name prefix is `myapp`. You can update `infra/parameters.*.json` to suitable names.

## Usage
- Clone this repo, set secrets, push to `develop` to deploy QA; merge to `main` to deploy PROD.
