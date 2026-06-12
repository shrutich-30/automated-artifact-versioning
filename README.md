# MINI PROJECT #06: Automated Artifact Versioning Pipeline 🚀

## Project Overview

This project implements an automated artifact versioning pipeline using GitHub Actions and Docker.

The main idea behind this project is to automate the complete release process. Whenever a new Git tag is created, GitHub Actions automatically builds a Docker image, assigns proper version tags, generates a changelog, and creates a GitHub Release.

This removes manual steps from the deployment process and provides a consistent way to manage application versions.

---

## Project Objective

The goal of this project is to create a CI/CD pipeline that:

* Automatically builds a Docker image
* Tags Docker images using semantic versions
* Tags images using Git commit SHA for tracking
* Creates automated GitHub Releases
* Generates release changelog
* Creates a versioned and deployable artifact

---

## Technologies Used

* **GitHub Actions** - Automation and CI/CD workflow
* **Docker** - Containerization of the application
* **Git** - Source code management and version tracking
* **Semantic Versioning** - Managing application releases
* **GitHub Releases** - Release automation

---

# Project Workflow

The complete pipeline works like this:

```
Developer makes changes
          |
          ↓
Commit changes to GitHub
          |
          ↓
Create version tag (v1.0.0)
          |
          ↓
GitHub Actions Trigger
          |
          ↓
Build Docker Image
          |
          ↓
Tag Image
(version + commit SHA)
          |
          ↓
Generate Changelog
          |
          ↓
Create GitHub Release
```

---

# Project Structure

```
automated-artifact-versioning/

│
├── app.py
├── requirements.txt
├── Dockerfile
│
└── .github
    └── workflows
        └── release.yml
```

---

# Concepts Applied

## 1. GitHub Actions

GitHub Actions is used to automate tasks directly inside the GitHub repository.

Instead of manually building Docker images and creating releases, the workflow automatically runs whenever a version tag is pushed.

Example:

```
git tag v1.0.0
git push origin v1.0.0
```

This triggers the pipeline automatically.

### Why it is useful:

* Reduces manual work
* Prevents human errors
* Creates consistent deployments
* Helps implement CI/CD practices

---

# 2. Docker Containerization

Docker is used to package the Flask application along with its dependencies into a portable container.

The Docker image contains:

* Application code
* Python environment
* Required libraries
* Runtime configuration

Example:

```
docker build -t artifact-versioning .
```

### Why it is useful:

* Application runs the same everywhere
* Easy deployment
* Better environment management
* Simplifies scaling

---

# 3. Semantic Versioning

Semantic versioning is a standard way to manage software releases.

Format:

```
MAJOR.MINOR.PATCH

Example:

v1.0.0
```

Meaning:

* Major → Breaking changes
* Minor → New features
* Patch → Bug fixes

Example:

```
v1.0.0

v1.0.1  (small update)

v1.1.0  (new feature)
```

### Why it is useful:

It helps developers and users understand what changed between releases.

---

# 4. Git Commit SHA Tagging

Every Git commit has a unique SHA value.

Example:

```
a83f92d7
```

The Docker image can also be tagged with this value.

Example:

```
artifact-versioning:v1.0.0

artifact-versioning:a83f92d7
```

### Why it is useful:

* Easy tracking of which code created an image
* Helps debugging
* Provides traceability between code and deployment

---

# 5. Automated Release Creation

The workflow automatically creates GitHub Releases after a version tag is pushed.

Each release contains:

* Version number
* Changelog
* Docker artifact

Example:

```
Release:

v1.0.1

Changes:
- Updated Flask response
- Improved application setup
```

### Why it is useful:

* Keeps release history organized
* Makes deployments easier
* Provides clear documentation of changes

---

# What I Understood From This Project

Before this project, deployment involved multiple manual steps:

* Building Docker image
* Naming versions
* Creating releases
* Maintaining change history

After implementing this pipeline, the complete release process became automated.

The main learning was understanding how modern software teams use CI/CD pipelines to automatically test, package, and release applications.

A simple Git tag can now trigger the complete release workflow.

---

# Benefits of This Pipeline

✅ Faster software delivery
✅ Automated release management
✅ Better version tracking
✅ Reduced manual errors
✅ Reproducible deployments
✅ Professional CI/CD workflow experience

---

# Future Improvements

Some improvements that can be added:

* Push Docker images to Docker Hub
* Add automated testing before release
* Add Kubernetes deployment after release
* Add security scanning for Docker images

---

# Conclusion

The Automated Artifact Versioning Pipeline demonstrates how GitHub Actions, Docker, and semantic versioning work together to create a reliable release automation system.

Every version tag creates a new deployable release automatically, similar to workflows used in real-world DevOps environments.
