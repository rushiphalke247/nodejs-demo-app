#  CI/CD pipeline to build and deploy a web app.

This project is a simple Node.js web application containerized with Docker and deployed through a **GitHub Actions CI/CD pipeline**.  
The pipeline automatically builds and tests the application, creates a Docker image, and pushes it to **DockerHub**.

**Flowchart how the project Work**

 Code Push → GitHub Actions → Run Tests → Build Docker Image → Push to DockerHub


 # Features
- Node.js + Express demo app
- Basic test script
- Dockerfile for containerization
- GitHub Actions workflow for CI/CD
- Automatic DockerHub image push

## Project Structure

nodejs-demo-app/
├─ .github/
│  └─ workflows/
│     └─ main.yml        # GitHub Actions workflow
├─ Dockerfile            # Container build instructions
├─ index.js              # Main app file
├─ package.json          # Node.js dependencies & scripts
├─ test.js               # Basic test
└─ README.md             # Project documentation

## Setup Instructions

### 1. Clone the repo
git clone https://github.com/rushiphalke247/nodejs-demo-app.git
cd nodejs-demo-app

### 2. Install dependencies
npm ci
### 3. Run locally
npm start

Visit [http://localhost:3000](http://localhost:3000) → you should see:

Hello from nodejs-demo-app!


## Docker
### Check Docker Login 
docker login

### Check docker image 
docker images 

### Run container
docker run -p 3000:3000 <your-dockerhub-username>/nodejs-demo-app:local
 
### Generate Personal Access Token in Docker
  **Account Settings --> Personal Tokens --> Generate**
 
## GitHub Actions CI/CD

The pipeline (`.github/workflows/main.yml`) runs on every push to the **main** branch:

1. Checkout code**
2. Install Node.js & dependencies**
3. Run tests** (`npm test`)
4. Login to DockerHub** (using GitHub Secrets)
5. Build & Push Docker image** to DockerHub


## Secrets Required in GitHub Repo
Go to
### Settings → Secrets and variables → Actions** and add:

* `DOCKERHUB_USERNAME` → your DockerHub username
* `DOCKERHUB_TOKEN` → your DockerHub access token (from DockerHub > Account Settings > Security > New Access Token)


## Verifying the Pipeline

* Check **Actions tab** in GitHub → workflow should show
* Go to [DockerHub](https://hub.docker.com/) → your repo should contain `nodejs-demo-app`
* Pull and run the pushed image:

  docker pull <your-dockerhub-username>/nodejs-demo-app:latest
  docker run -p 3000:3000 <your-dockerhub-username>/nodejs-demo-app:latest

**CI/CD** → Automates building, testing, and deploying code.
**GitHub Actions** → Event-driven workflows for automation.
**Docker** → Packages the app into a portable container image.
**DockerHub** → Public/private registry to store and distribute Docker images.

