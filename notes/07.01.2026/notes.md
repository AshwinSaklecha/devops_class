# GitHub Actions - Self-Hosted Agents and CD

## Self-Hosted Runners
- Run workflows on your own machines
- More control over environment
- Access to private resources

## Setting Up Self-Hosted Runner
1. Go to repo Settings > Actions > Runners
2. Click "New self-hosted runner"
3. Follow installation steps
4. Run the config script

## Using Self-Hosted Runner
```yaml
jobs:
  deploy:
    runs-on: self-hosted
    steps:
    - uses: actions/checkout@v3
    - name: Deploy
      run: ./deploy.sh
```

## CD Pipeline Example
```yaml
name: CD Pipeline

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Build Docker image
      run: docker build -t myapp:${{ github.sha }} .
    - name: Push to registry
      run: docker push myapp:${{ github.sha }}

  deploy:
    needs: build
    runs-on: self-hosted
    steps:
    - name: Deploy to K8s
      run: kubectl set image deployment/myapp myapp=myapp:${{ github.sha }}
```

## Key Points
- Use `needs` for job dependencies
- Self-hosted for private deployments
- Use secrets for credentials
- Tag images with commit SHA
