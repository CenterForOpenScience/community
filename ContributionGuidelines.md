# Contribution Guidelines

## 1. Introduction

Thank you for your interest in contributing to the **Open Science Framework (OSF)**!  
OSF is an open-source platform dedicated to enhancing research transparency, reproducibility, and collaboration.

Contributions from the community help improve OSF and make open science more accessible to researchers worldwide. Whether you are a developer, researcher, or open science advocate, your contributions are valued and appreciated.

---

## 2. Code of Conduct

All community members must adhere to the **[OSF Code of Conduct](https://www.cos.io/events-code-of-conduct)**, which outlines expected behavior and guidelines for respectful interactions.

The Code of Conduct applies to all contributors, maintainers, and users engaging with the OSF community.  
Please review it before participating.

---

## 3. How to Contribute

There are several ways to contribute to OSF:

### 3.1 Reporting Issues

If you encounter a bug, have a feature request, or want to provide feedback, open an issue in the OSF GitHub repository.

Please:

- Provide a clear and descriptive title
- Include steps to reproduce the issue (if applicable)
- Suggest possible solutions or workarounds
- Use the issue reporting template for guidance

### 3.2 Submitting Code Contributions

Code contributions are made through pull requests (PRs).

Steps:

1. Fork the OSF repository and create a local branch
2. Follow OSF’s coding standards and best practices
3. Write tests for your code when applicable
4. Submit a pull request with a detailed description of your changes  
   (use the pull request template for guidance)
5. Respond to comments and participate in the review process

### 3.3 Improving Documentation

Documentation contributions are just as valuable as code!

You can help by:

- Updating existing documentation for clarity and completeness
- Writing new guides to help users navigate OSF features
- Fixing broken links or outdated information

> Note: Due to the structure of the GitHub org under `CenterForOpenScience`, review processes may vary.  
> Please contact a team member on [Discord](https://discord.gg/KDWasAks5y) to discuss your suggestions and the review process.

### 3.4 Developing Add-Ons

OSF supports a modular architecture—contribute by building add-ons that integrate with OSF!

Add-ons extend OSF's capabilities (e.g., storage integrations, citation managers, analytics tools).

**Languages used**:
- Backend: Python
- Frontend: Ember (migrating to Angular, completion expected Sept 2025), TypeScript/JavaScript, HTML/CSS

To create a new add-on:

- Learn about the [OSF Add-ons Service](#) and how it interacts with the platform
- Explore **GravyValet**, OSF’s third-party integration service
- Review existing add-ons for architecture and style
- Follow OSF coding standards and ensure your code is modular and well-documented

**Official add-on maintainership**:

- You (or a delegate) must commit to maintain the add-on for at least 1 year
- Responsibilities include addressing issues, updating dependencies, and ensuring compatibility with OSF

We greatly appreciate contributions to the OSF add-on ecosystem!

---

## 4. Contribution Review Process

### 4.1 Reviewing Contributions

Maintainers review all submissions for:

- Quality
- Relevance
- Adherence to contribution guidelines

Contributors are encouraged to engage in the review process through comments and suggestions.

### 4.2 Merging and Releasing Contributions

OSF follows a structured merge/release process:

1. PRs are merged into a feature branch (not directly into `master`)
2. The feature branch is deployed to staging for QA and product review
3. Once approved, the feature branch is merged into `master`
4. Updates are released in scheduled deployment cycles

This ensures quality, prevents regressions, and aligns changes with project priorities.

> Contributors may be asked to collaborate during QA testing if issues arise.

### 4.3 Acknowledging Contributions

All contributors are credited for their work:

- Tagged upon merging with the main branch
- Featured by the OSF marketing team in release announcements (with contributor permission)

---

## 5. Community Roles

### 5.1 Users

Interact with OSF features, provide feedback, and report issues.

### 5.2 Contributors

Submit code, update documentation, and review others’ contributions.

### 5.3 Maintainers

Experienced contributors who review and merge PRs, manage releases, and support community collaboration.

### 5.4 OSF Product Owners

COS staff managing the OSF roadmap, prioritization, and overall development.

### 5.5 Steering Committee

Guides OSF’s direction, resolves disputes, and makes governance decisions.

---

## 6. Project Roadmap & Management

The OSF roadmap and plans are publicly available in our [governance documentation](#) or via shared links.  
Please stay up to date by reviewing the roadmap periodically.

---

## 7. Overview of OSF Tools

OSF is a modular platform designed to support all stages of research:

- **OSF Core Platform (`osf.io`)**: Central research management hub
- **AngularJS**: Front-end framework (transitioning to Angular)
- **WaterButler**: Handles file storage interactions
- **GravyValet**: Connects OSF with external services like cloud storage and citation managers

These components interact through APIs to facilitate collaboration, data sharing, and transparency.

> See our [technical documentation](https://developer.osf.io/) for details.

---

## 8. Getting Started

- Join the OSF community by watching and participating in this repo
- Choose a contribution pathway that fits your skills
- Follow OSF’s contribution standards
- Reach out to maintainers for support and feedback

---

Thank you for helping us build tools that support open, transparent, and reproducible science!  
We look forward to collaborating with you 🚀
