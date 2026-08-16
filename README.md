# Detection as Code (DaC) Pipeline

## Overview
This repository serves as a centralized, version-controlled library for security detection rules. By utilizing Detection as Code (DaC) principles, detection logic is decoupled from specific SIEM platforms and written in the universally standardized [Sigma](https://sigmahq.io/) format (YAML). 

This allows for vendor-neutral rule creation that can be programmatically translated and deployed to various platforms.

## 🚀 CI/CD Automation
This project is equipped with an automated GitHub Actions pipeline to ensure code quality and prevent broken logic from entering production. 

Every time a new rule is pushed or modified, the pipeline automatically:
* **Triggers** on pushes to the `main` branch.
* **Lints** the YAML code strictly using `yamllint` to prevent malformed syntax, incorrect spacing, and structural errors.
* **Validates** integrity before any potential deployment scripts are run.

## 📁 Repository Structure

```text
.
├── .github/workflows/
│   └── validate.yml       # The GitHub Actions CI/CD pipeline
├── bruteforce.yml         # Sigma detection rules
└── README.md              # Project documentation

✍️ How to Add a New Rule
All rules must be written in valid YAML and follow the standard Sigma schema.
Create a new .yml file in the root directory (e.g., suspicious_powershell.yml).
Ensure the file begins with the --- document start marker.
Define your detection logic using standard Sigma fields (title, status, description, logsource, detection).
Save, commit, and push to trigger the automated validation pipeline.
