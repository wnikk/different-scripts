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
