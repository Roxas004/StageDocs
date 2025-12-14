# QA - GitLab

This document provides guidelines and best practices for using **GitLab** effectively within the project. GitLab is a complete DevOps platform that offers Git repository management, continuous integration (CI), issue tracking, and team collaboration features.

## 1. Overview

**GitLab** is a version control tool based on Git, integrated with a comprehensive suite of DevOps services. It allows you to:

- Manage source code via Git repositories  
- Collaborate through Merge Requests and Issues  
- Set up CI/CD pipelines to automate testing and deployments  
- Track bugs, tasks, and project enhancements  
- Manage user permissions and repository security  

### Advantages of GitLab

- **Integrated CI/CD:** Streamlines testing and deployment with centralized configuration.
- **User-friendly Interface:** Simplifies code management and team collaboration.
- **Granular Permission Control:** Allows fine-tuned access management with roles.
- **Enhanced Collaboration:** Supports merge requests, code reviews, and efficient issue tracking.
- **Rich Ecosystem:** Provides comprehensive documentation and a vibrant community.

## 2. Project Setup

### a. Creating a Merge Request

1. Navigate to your GitLab repository  
2. Go to “Merge Requests” > “New Merge Request”  
3. Select the source branch and the target branch (`main` or `develop`)  
4. Provide a clear description of the changes, optionally link an issue (e.g., `Closes #123`), and assign reviewers  

## 4. Issue Management

- Create one issue per task, bug, or enhancement  
- Use labels, milestones, and assignees to organize issues  
- Add checklists to track sub-tasks when needed  

## 5. Continuous Integration (CI/CD)

### a. The `.gitlab-ci.yml` File

Define your CI pipeline in this file at the root of the project. Example:

```yaml
stages:
  - test

phpunit:
  stage: test
  script:
    - composer install
    - vendor/bin/phpunit
```

### b. Pipelines

- Every push or merge request triggers a pipeline  
- Results are displayed under “CI/CD > Pipelines” in GitLab  

## 6. Best Practices

- Follow naming conventions for branches:  
  `feature/`, `fix/`, `hotfix/`, `refactor/`, etc.

- Always work on a **separate branch** from `main` or `develop`

- Create **clear and descriptive merge requests**: include full details, clean code, and well-organized commits

- Use **CI/CD pipelines** to test before merging

- Encourage **code reviews** to improve project quality and collaboration

## 7. Permissions and Security

- Assign roles as needed: Guest, Reporter, Developer, Maintainer, Owner  
- Enable branch protection for important branches (`main`, `release`, etc.)  
- Require merge request approvals to enforce peer review before merging  

## 8. Useful Resources

- GitLab Documentation: [https://docs.gitlab.com](https://docs.gitlab.com)  
- Git Guide: [https://git-scm.com/doc](https://git-scm.com/doc)  
- Git Cheat Sheet: [https://education.github.com/git-cheat-sheet-education.pdf](https://education.github.com/git-cheat-sheet-education.pdf)

