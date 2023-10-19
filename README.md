# Python App Deployment using Github Actions

## Overview:
I have created a basic Python app, with task to deploy it using Github Actions. 

## Installation Guide:
To start the app on your local machine make sure to have git, docker & docker-compose already installed.

### Clone the Repo
```sh
git clone https://github.com/shaggyyy2002/demo-pipeline.git
```

### Start app Using Docker
- Build Docker Image: 
```sh
docker build -t python-app . 
```
- Run Docker Image as Container: 
```sh
docker run -d -p 5000:5000 --name pearlthoughts python-app 
```

### OR

### Start using Docker-Compose 
- Make sure you're in the root folder and paste the command in your terminal
```sh
docker-compose up
```

## CI-CD Pipeline

**CI Pipeline:** 

- Our CI Pipeline helps us to build and push our Docker Image to our Personal Repository.
- It creates a push everytime we add something to our main branch.
- We have also setup our Docker Login credentials onto our Github Secrets. 
- Once all the process is done it pushed our dockerimage to our `nitin03/python-app` repo on DockerHub with a `latest` tag. 

**CD Pipeline:** 

- Once the CI pipeline is done only then our CD pipeline will start running because of the `workflow_run`.
- To run our docker image as a container we have setup our self hosted runner onto our Github Repo. 
- The next steps our Pipeline will follow are
     
     - Pull the docker-image from our DockerHub repo. 
     - Delete our old container running the same image if any. 
     - Once done it will start a new contaier using the latest Docker-Image from our DockerHub.

## Post Deployment
<img width="440" alt="Screenshot 2023-10-19 at 4 40 03 PM" src="https://github.com/shaggyyy2002/demo-pipeline/assets/90847875/24166400-6a85-4640-8383-c926770aeb04">



