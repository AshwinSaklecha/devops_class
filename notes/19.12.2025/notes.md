# GitHub Actions - Simple CI Pipeline

## What is GitHub Actions?
- CI/CD platform by GitHub
- Automate workflows on GitHub events
- Free for public repos

## Key Concepts
- **Workflow** - Automated process defined in YAML
- **Job** - Set of steps in workflow
- **Step** - Individual task in job
- **Action** - Reusable workflow component

## Workflow File Location
- `.github/workflows/` directory
- YAML format

## Basic Workflow Example
```yaml
name: CI Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.9'
    
    - name: Install dependencies
      run: pip install -r requirements.txt
    
    - name: Run tests
      run: pytest
```

## Common Triggers
- push - on code push
- pull_request - on PR created
- schedule - cron based
- workflow_dispatch - manual trigger

## Secrets
- Store sensitive data in Settings > Secrets
- Access using `${{ secrets.SECRET_NAME }}`
