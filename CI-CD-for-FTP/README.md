# GitLab CI/CD for FTP Deployment

## 📌 Overview
This `GitLab CI/CD` pipeline automates the deployment of web projects to a remote server via **FTP**.  
It includes **build**, **testing**, **production deployment**, **automatic backups**, and **rollback capabilities**.

## 🚀 Features
✅ **Automated project build**  
✅ **PHP syntax validation before deployment**  
✅ **Seamless file updates without data loss**  
✅ **Backup creation before each deployment**  
✅ **Rollback option to restore previous versions**  
✅ **Automatic cleanup of outdated backups**  

## 📂 Pipeline Structure

| Stage          | Description |
|---------------|-------------------------------------|
| `build`       | Compiles and prepares files |
| `test`        | PHP syntax validation |
| `test-deploy` | Deployment to a test environment |
| `prod-refresh` | Fast update production without backup |
| `prod-deploy` | Full deployment with backup |
| `prod-rollback` | Restores the previous version |

## ⚙ Environment Variables
Before using this pipeline, ensure you have set up the following **GitLab CI/CD environment variables** for FTP access:

```yaml
variables:
  FTP_HOST: "$CI_FTP_HOST"
  FTP_USERNAME: "$CI_FTP_USERNAME"
  FTP_PASSWORD: "$CI_FTP_PASSWORD"

**Important:** Do not store passwords directly in `.gitlab-ci.yml`, use GitLab’s CI/CD secret variables like `$CI_FTP_PASSWORD`.

## 🏗 Setup & Usage
### 1️⃣ **Add `.gitlab-ci.yml` to your repository root**  
Place the `gitlab-ci.yml` file in your project's repository.

### 2️⃣ **Configure GitLab CI/CD variables**  
Go to **Settings > CI/CD > Variables**, then add:
- `CI_FTP_HOST`
- `CI_FTP_USERNAME`
- `CI_FTP_PASSWORD`

### 3️⃣ **Trigger the pipeline in GitLab**  
Whenever you push a commit to `main`, the pipeline will **automatically** execute build and deployment.

## 🔄 Rollback to a Previous Version
If the new version fails, restore the previous version.
This reverts the deployment to the last working backup stored in version_last.

## 📖 How It Works
1. **Build phase** prepares files in `dist/`.  
2. **Test phase** validates PHP syntax before deployment.  
3. **Production deployment** updates files **via FTP**.  
4. **Backup creation** saves the previous version in `version_lastYYYYMMDD_HHMM`.  
5. **Rollback mechanism** restores the last working version.  

📌 This repository serves as a **template** for CI/CD deployment via FTP, and can be customized for various use cases.

