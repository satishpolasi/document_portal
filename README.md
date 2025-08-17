# Project Setup Guide

## Create Project Folder and Environment Setup

```bash
# Create a new project folder
mkdir <project_folder_name>

# Move into the project folder
cd <project_folder_name>

# Open the folder in VS Code
code .

# Create a new Conda environment with Python 3.10
conda create -p <env_name> python=3.10 -y

# Activate the environment (use full path to the environment)
conda activate <path_of_the_env>

# Install dependencies from requirements.txt
pip install -r requirements.txt

# Initialize Git
git init

# Stage all files
git add .

# Commit changes
git commit -m "<write your commit message>"

# Push to remote (after adding remote origin)
git push

# Cloning the repository
git clone https://github.com/satishpolasi/document_portal.git

# command for executing the fast api
uvicorn api.main:app --reload

```
## Minimum Requirements for the Project

### LLM Models
- **Groq** (Free)
- **OpenAI** (Paid)
- **Gemini** (15 Days Free Access)
- **Claude** (Paid)
- **Hugging Face** (Free)
- **Ollama** (Local Setup)

### Embedding Models
- **OpenAI**
- **Hugging Face**
- **Gemini**

### Vector Databases
- **In-Memory**
- **On-Disk**
- **Cloud-Based**

# AWS secret Manager is the industry practice to store API Keys instead of .env file

# API Keys

### GROQ API Key
- [Get your API Key](https://console.groq.com/keys)  
- [Groq Documentation](https://console.groq.com/docs/overview)

### Gemini API Key
- [Get your API Key](https://aistudio.google.com/apikey)  
- [Gemini Documentation](https://ai.google.dev/gemini-api/docs/models)

### Testing steps of docker image in local system
1. Download the Docker desktop in your system
2. Install the docker in your system
3. Run the docker engine in your system
4. First create the docker file inside your project folder

Test your docker with the below command
1. docker
2. docker version
3. docker help
4. docker ps -- to lis running containers/images
4. docker ps -a -- to list all the containers/iamges

5. Build the image from your current project repo
command to build docker image - Build Docker Image
Command to create  the docker image
- docker build -t document-portal-system . (here . is the current directory)
command to check docker images 
- docker images

6. Run this image inside the container
Run the image inside the docker container

- docker run -d -p 8093:8080 --name my-doc-portal document-portal-system

7. If everything is running then push the image to your docker hub[optional step]

To push a Docker image from your local Docker Desktop to Docker Hub, follow these steps:

1. Log in to Docker Hub
docker login

Enter your Docker Hub username and password/token.

2. Check your local images
docker images

Example output:

REPOSITORY     TAG       IMAGE ID       CREATED       SIZE
my-app         latest    7d9495d03763   2 hours ago   150MB

3. Tag the image for Docker Hub

Docker Hub requires the format:
<dockerhub-username>/<repository>:<tag>

docker tag my-app:latest your-dockerhub-username/my-app:latest

Example (if your Docker Hub username is tanisi):

docker tag my-app:latest tanisi/my-app:latest

4. Push the image
docker push your-dockerhub-username/my-app:latest

Example:

docker push tanisi/my-app:latest

✅ After this, the image will be available on Docker Hub under your account.
You can then pull it from anywhere using:

docker pull your-dockerhub-username/my-app:latest


Then after testing will start the deployment
1. Github Action[will have to write the yaml config]
2. ECR[ecr for containing the docker image similar to docker hub but it is AWS native service]
3. ECS + Fargate [this is for the image orchestration it is a serverless service of aws]