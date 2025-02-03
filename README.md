# Example repo to run a web application using Docker and push to image registry with Github Action CI pipeline

**Please star this repository **

1. Clone the repo

```
git clone https://github.com/tyagian/cicd_example.git
```

2. Build the Docker image
```
docker build -t flask-webserver .
```

3. Run the Container
```
docker run -p 5000:5000 flask-webserver
```

4. Test from browser
```
Open the Webpage http://localhost:5000
```
This setup provides a fully functional Flask web server with a responsive homepage, all running inside a Docker container.

# CI Pipeline with Github Actions

1. Inside your GitHub repository, create the following directory and file:
```
.github/workflows/docker-build.yml
```

2. This workflow automates the build and trigger pipeline whenever you push code to the main branch.

3. Setting Up Secrets in GitHub
a. Go to your repository on GitHub.
b. Navigate to Settings → Secrets and variables → Actions.
c. Click New repository secret and create a secret:
`Name:` GHCR_TOKEN
`Value:` A GitHub Personal Access Token (PAT) with the following 
`read: packages` 
`write: packages` 
`delete: packages` 

4. After the GitHub Action runs successfully, you can pull & run the container using:
```
docker pull ghcr.io/<your-github-username>/flask-webserver:latest

docker run -p 5000:5000 ghcr.io/<your-github-username>/flask-webserver:latest
```
