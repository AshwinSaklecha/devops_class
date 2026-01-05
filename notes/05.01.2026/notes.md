# DevSecOps Introduction

## What is DevSecOps?
- Security integrated into DevOps pipeline
- Shift-left approach - security early in SDLC
- Security is everyone's responsibility

## Traditional vs DevSecOps
- Traditional: Security at the end (too late, expensive fixes)
- DevSecOps: Security throughout the pipeline

## Security in CI/CD Pipeline

### SAST (Static Application Security Testing)
- Analyze source code for vulnerabilities
- Tools: SonarQube, Semgrep, Bandit
- Run during build phase

### SCA (Software Composition Analysis)
- Check dependencies for vulnerabilities
- Tools: Snyk, Dependabot, OWASP Dependency Check

### DAST (Dynamic Application Security Testing)
- Test running application
- Tools: OWASP ZAP, Burp Suite
- Run in staging environment

### Container Scanning
- Scan Docker images for vulnerabilities
- Tools: Trivy, Clair, Anchore

## Implementing DevSecOps
1. Add SAST to build stage
2. Add SCA for dependency check
3. Scan container images before push
4. DAST in staging
5. Security gates in pipeline

## Key Practices
- Automate security checks
- Fail builds on critical vulnerabilities
- Regular security updates
- Security training for devs
