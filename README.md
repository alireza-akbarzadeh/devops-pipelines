# GitHub Actions DevOps Pipeline

This repository serves as a personal reference to learn and document everything related to GitHub Actions and DevOps pipelines. The goal is to create workflows and pipelines, explore automation, and get hands-on experience with GitHub CI/CD.

## Table of Contents

1. [Introduction](#introduction)
2. [Repository Structure](#repository-structure)
3. [GitHub Actions Overview](#github-actions-overview)
4. [Setting Up GitHub Actions](#setting-up-github-actions)
5. [Example Workflows](#example-workflows)

   * [Basic CI Pipeline](#basic-ci-pipeline)
   * [Build and Test Workflow](#build-and-test-workflow)
6. [Common Issues and Troubleshooting](#common-issues-and-troubleshooting)
7. [Learning Resources](#learning-resources)
8. [License](#license)

---

## Introduction

Welcome to my GitHub Actions DevOps repository! Here, I am exploring and experimenting with GitHub Actions for Continuous Integration (CI) and Continuous Deployment (CD). This repo contains example workflows, scripts, and configurations to automate tasks such as testing, building, and deploying applications.

---

## Repository Structure

Here’s a quick breakdown of the folder structure in this repository:

```
.github/
  workflows/
    pipeline.yaml  # GitHub Actions pipeline configuration file
index.js           # Sample JavaScript code
test.js             # Sample test file
package.json        # Node.js package configuration
README.md           # This file
```

---

## GitHub Actions Overview

GitHub Actions allows you to automate, customize, and execute your software development workflows right in your repository. It helps in automating tasks such as:

* Continuous Integration (CI)
* Continuous Deployment (CD)
* Running Tests
* Automating Deployments
* Managing releases, and much more...

---

## Setting Up GitHub Actions

### Step 1: Create the Workflow Directory

Create a `.github/workflows` directory at the root of your repository.

### Step 2: Create the Workflow YAML File

In the `workflows` directory, create a YAML file (e.g., `pipeline.yaml`) where you will define your CI/CD pipeline. Here's an example:

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
      - name: Checkout code
        uses: actions/checkout@v5
      
      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

### Step 3: Commit and Push

Commit the `.github` directory and YAML file to your repository, then push the changes to GitHub. Once pushed, you should be able to see the workflow in the **Actions** tab of your GitHub repository.

---

## Example Workflows

### Basic CI Pipeline

A basic pipeline with steps to checkout code, install dependencies, and run tests:

```yaml
name: Basic CI Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
      - name: Checkout code
        uses: actions/checkout@v5

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

### Build and Test Workflow

A more advanced pipeline where you might run unit tests and linting checks, as well as build the project:

```yaml
name: Build and Test

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v5

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'

      - name: Install dependencies
        run: npm install

      - name: Run lint checks
        run: npm run lint

      - name: Run tests
        run: npm test

      - name: Build project
        run: npm run build
```

---

## Common Issues and Troubleshooting

### 1. Workflow not triggering

* Ensure that the YAML file is located in `.github/workflows/` directory.
* Make sure your `on.push` triggers are correctly configured (e.g., to the `main` branch).

### 2. "Action not found" error

* Verify that you have correctly referenced the action version (e.g., `actions/checkout@v5`).
* Ensure that there are no typos in the action names.

### 3. "Dependency not found" error

* Check that `npm install` is correctly run before attempting to run tests or build the project.
* Ensure all dependencies are listed in `package.json`.

---

## Learning Resources

* [GitHub Actions Documentation](https://docs.github.com/en/actions)
* [CI/CD with GitHub Actions](https://www.freecodecamp.org/news/ci-cd-with-github-actions/)
* [YouTube GitHub Actions Tutorials](https://www.youtube.com/results?search_query=github+actions+tutorial)
* [GitHub Actions for CI/CD](https://www.digitalocean.com/community/tutorials)

---

## License

This repository is for personal learning purposes only. Feel free to fork or clone this repository for your learning, but ensure to give proper credit if you reuse any of the content.

---

### Final Thoughts

Now that you've set up this repository and learned how to create your GitHub Actions workflows, you can explore more complex use cases, like deploying applications, handling secrets, integrating third-party actions, and much more. This will become a personal reference guide to keep your DevOps knowledge fresh and handy for future projects!

Let me know if you need help expanding or customizing this README further!
