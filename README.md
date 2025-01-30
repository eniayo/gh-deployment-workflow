# Log Archive Tool

## GitHub Pages Deployment Workflow

### Overview
This project demonstrates the concept of **Continuous Integration and Continuous Deployment (CI/CD)** by using **GitHub Actions** to deploy a static website to **GitHub Pages**. The workflow is triggered by changes to the `index.html` file in the `main` branch.

### Features
- **Automatic Deployment**: Deploys changes to GitHub Pages whenever `index.html` is updated.
- **Continuous Integration**: Ensures that any changes made to `index.html` are automatically integrated and deployed.

---

## Requirements
- A **GitHub account**
- A **public GitHub repository**

---

## Getting Started

### Step 1: Create a GitHub Repository
1. Create a new **public repository** on GitHub called `gh-deployment-workflow`.
2. Add a simple `index.html` file with the content:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>GitHub Actions Deployment</title>
    </head>
    <body>
        <h1>Hello, GitHub Actions!</h1>
    </body>
    </html>
    ```

3. Add a `README.md` file explaining the project.

---

### Step 2: Create GitHub Actions Workflow
1. In your repository, create a directory called `.github/workflows`.
2. Inside the `workflows` directory, create a file named `deploy.yml`.

#### Example `deploy.yml`
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main
    paths:
      - 'index.html'

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Setup Pages
        id: pages
        uses: actions/setup-pages@v1

      - name: Upload artifact
        uses: actions/upload-artifact@v2
        with:
          name: page
          path: ./

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

> **Note:** This workflow triggers a deployment whenever the `index.html` file is modified in the `main` branch.

---

### Step 3: Push Changes to GitHub
Run the following commands in your terminal to initialize the repository and push changes:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/yourusername/gh-deployment-workflow.git
git push -u origin main
```

> **Replace `yourusername`** with your actual GitHub username.

---

### Step 4: Access Your Website
Once the workflow runs successfully, your website will be accessible at:

```
https://<username>.github.io/gh-deployment-workflow/
```

> **Replace `<username>`** with your actual GitHub username.

---

## Stretch Goals
To make this project more practical, consider using a **static site generator** such as:
- **Hugo**
- **Jekyll**
- **Astro**

This will allow you to create a **more complex website**, such as your personal **portfolio**.

---

## Learning Outcomes
By completing this project, you will gain a solid understanding of:
- **GitHub Actions**
- **GitHub Pages**
- **Continuous Integration (CI)**
- **Continuous Deployment (CD)**
- **Writing GitHub Actions workflows**

---

## License
This project is licensed under the **MIT License**.
