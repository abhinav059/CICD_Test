# TASK 10  CI/CD Pipeline AND Notification ussing SLACK
## DEMO VIDEO LINK - https://drive.google.com/file/d/1CNx_2JzpxJGB26ypnTlLrMKgk1SweetG/view?usp=sharing

## Overview
This CI/CD pipeline is designed to automate integrating testing, security scanning, and deployment to multiple environments (staging and production). Additionally, Slack notifications are implemented to alert the team about pipeline events and security issues.

---

## Features
- **Automated Testing**: Runs unit tests using `pytest`.
- **Security Scanning**: Uses `bandit` to detect security vulnerabilities.
- **Staging Deployment Simulation**: Ensures the code is ready before moving to production.
- **Production Deployment Simulation**: Confirms successful delivery to production.
- **Slack Notifications**: Alerts team members about deployment status and security issues.

---

## Pipeline Workflow

### Step 1: Run Tests
- The pipeline runs unit tests using `pytest`.
- If tests fail, the pipeline stops and does not proceed further.

### Step 2: Security Scanning
- The security scan uses `bandit` to check for vulnerabilities in Python code.
- If vulnerabilities are detected, a Slack notification is sent.

### Step 3: Staging Deployment Simulation
- If the security scan passes, the code is deployed to the staging environment.
- This step ensures that the application functions correctly before production.

### Step 4: Production Deployment Simulation
- After staging verification, the code is deployed to the production environment.

### Step 5: Slack Notifications
- A notification is sent after successful deployment.
- If security issues are found, another notification alerts the team.

---

## Setup & Execution

### **Prerequisites**
- A GitHub repository with a `requirements.txt` file.
- A `pytest` test suite for automated testing.
- A GitHub Actions workflow file (`.github/workflows/cicd.yml`).
- A Slack webhook URL stored as a GitHub secret (`SLACK_WEBHOOK`).

### **Step-by-Step Execution**
1. **Commit and push code to the repository**
   ```sh
   git add .
   git commit -m "Initial commit with CI/CD setup"
   git push origin main
   ```

2. **GitHub Actions triggers the pipeline automatically**
   - The pipeline starts with **unit testing**.
   - If tests pass, it proceeds to **security scanning**.
   - If no security issues are found, deployment begins.
   - Finally, Slack notifications are sent to the team.
   - ![](https://github.com/abhinav059/Screenshots/blob/main/10T.png)


3. **Monitor GitHub Actions logs**
   - Navigate to your repository.
   - Go to **Actions** → Select the running workflow to check logs.

4. **Check Slack for deployment updates**
   - Successful deployment messages are sent.
   - If security issues arise, a warning notification is sent.

  ![](https://github.com/abhinav059/Screenshots/blob/main/10T2.png)


---

## Rollback Strategy
If a security issue is detected, the pipeline halts further deployment and alerts the team to resolve vulnerabilities before retrying the deployment.

---

## Conclusion
This CI/CD pipeline ensures:
- **Automated validation** through testing and security checks.
- **Safe deployment** via staging and production environments.
- **Instant notifications** for better team communication.
