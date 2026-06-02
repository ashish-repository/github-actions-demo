# GitHub Actions - Sample CI Pipeline

## Objective

Configure a basic GitHub Actions workflow that runs automatically whenever code is pushed to the `main` branch.

## Step 1: Create a GitHub Repository

Click:
'''
New Repository
'''
Example:
'''
Repository Name: github-actions-demo
Visibility: Public
'''
Click:
'''
Create Repository
'''

## Step 2: Clone Repository
'''
git clone https://github.com/<your-username>/github-actions-demo.git
'''

Move into the repository:
'''
cd github-actions-demo
'''

## Step 3: Create Workflow Directory

GitHub Actions only recognizes workflows inside:
'''
.github/workflows/
'''

Create it:
'''
mkdir -p .github/workflows
'''

## Directory Structure

```text
.github/
└── workflows/
    └── ci-pipeline.yml
```

## Sample GitHub Actions Workflow

File: `.github/workflows/ci-pipeline.yml`

```yaml
name: CI Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Source Code
        uses: actions/checkout@v4

      - name: Display Date
        run: date

      - name: Display Workspace Files
        run: ls -ltr

      - name: Create Demo File
        run: |
          mkdir demo
          cd demo
          echo "Hello from GitHub Actions" > test.txt
          cat test.txt

      - name: Workflow Completed
        run: echo "Pipeline executed successfully"
```

## Deploy the Workflow

```bash
git add .
git commit -m "Added GitHub Actions pipeline"
git push origin main
```

## Verify Execution

1. Open GitHub Repository.
2. Click **Actions** tab.
3. Select **CI Pipeline**.
4. View job logs.

## Expected Output

```text
Hello from GitHub Actions
Pipeline executed successfully
```

## Real-Time CI/CD Flow

```text
Developer Pushes Code
          ↓
GitHub Repository
          ↓
GitHub Actions Triggered
          ↓
Build
          ↓
Test
          ↓
Docker Build (Optional)
          ↓
Deploy to Kubernetes/AWS (Optional)
```

## Conclusion

GitHub Actions automates software delivery. In real projects, the pipeline typically performs code checkout, build, testing, Docker image creation, image push to a registry, and deployment to Kubernetes environments.
