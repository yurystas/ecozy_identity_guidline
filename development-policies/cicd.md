# CI/CD Pipeline

1. ### Infrastructure {#infrastructure}

**Text:** Our CI/CD pipeline is built on GitLab CI, using dedicated GitLab Runners hosted in our AWS environment. These runners are configured to use Docker, allowing us to define and manage build environments as code (`.gitlab-ci.yml`). This ensures a consistent, reproducible build, test, and deployment process across all microservices (backend, firmware, mobile).

2. ### Source Code Repositories {#source-code-repositories}

**Text:** GitLab serves as our single source of truth for all code. We adhere to a **GitFlow-based branching model**:

* **`main`**: This branch represents the latest production-ready code. All merges require a successful pipeline and approval.  
* **`develop`**: The primary integration branch for new features. This branch is deployed to our staging environment.  
* **`feature/*`**: All new work (features, improvements) must be done in a `feature/` branch (e.g., `feature/JIRA-123-new-auth`).  
* **`release/*`**: Used to prepare a new production release. Code freezes and final regression testing happen here.  
* **`hotfix/*`**: Used for urgent bug fixes required in production.

  3. ### Release Process {#release-process}

**Text:**

1. **Staging:** When a `feature/` branch is merged into `develop`, a pipeline automatically builds, tests, and deploys the service to the Staging environment.  
2. **Release:** To create a new release, a `release/` branch is cut from `develop`. The pipeline deploys this to a pre-production environment for final QA and regression testing.  
3. **Production:** Once the `release/` branch is stable and approved, it is merged into `main`. This merge triggers the final production deployment pipeline, which includes tagging the release in Git.
