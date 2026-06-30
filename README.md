# Dockerized Node.js Application on AWS EC2

A simple Node.js web application containerized with Docker and deployed on an Amazon EC2 Ubuntu instance. The Docker image is published on Docker Hub, demonstrating a complete container deployment workflow.

---

## Project Overview

This project demonstrates how to:

- Launch an Amazon EC2 Ubuntu instance
- Connect securely using SSH
- Install and configure Docker
- Build a Docker image for a Node.js application
- Run the application inside a Docker container
- Expose the application to the internet
- Publish the Docker image to Docker Hub

---

## Architecture

```
                +------------------+
                |    Developer     |
                +------------------+
                         |
                         | Git / SSH
                         |
                         ▼
              +----------------------+
              |   AWS EC2 (Ubuntu)   |
              +----------------------+
                         |
                  Docker Engine
                         |
                         ▼
              +----------------------+
              | Node.js Docker Image |
              +----------------------+
                         |
                         ▼
              +----------------------+
              | Docker Container     |
              | Port 3000            |
              +----------------------+
                         |
                         ▼
                 Web Browser
```

---

## Technologies Used

- AWS EC2
- Ubuntu 24.04 LTS
- Docker
- Node.js
- Git
- Docker Hub

---

## Project Structure

```
docker-nodejs-ec2/
│
├── app.js
├── package.json
├── Dockerfile
├── .gitignore
├── README.md
└── screenshots/
    ├── browser.png
    ├── docker-build.png
    ├── docker-running.png
    ├── dockerhub.png
    └── ec2-instance.png
```

---

## Dockerfile

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

---

## Build the Docker Image

```bash
docker build -t docker-nodejs-app .
```

---

## Run the Container

```bash
docker run -d -p 3000:3000 --name node-app docker-nodejs-app
```

Verify the container:

```bash
docker ps
```

---

## Test the Application

From the EC2 instance:

```bash
curl http://localhost:3000
```

Expected output:

```html
<h1>Docker Node.js App</h1>
<p>Successfully deployed on AWS EC2 using Docker!</p>
```

---

## Docker Hub Repository

Docker Image:

```text
tevinportfolio/docker-nodejs-app
```

Pull the image:

```bash
docker pull tevinportfolio/docker-nodejs-app:latest
```

Run directly from Docker Hub:

```bash
docker run -d -p 3000:3000 tevinportfolio/docker-nodejs-app
```

---

## Deployment Steps

1. Launch an Ubuntu EC2 instance
2. Configure Security Groups (Ports 22 and 3000)
3. Connect using SSH
4. Install Docker
5. Create the Node.js application
6. Build the Docker image
7. Run the Docker container
8. Verify the application
9. Push the image to Docker Hub

---

## Screenshots

### Application Running

![Application](screenshots/browser.png)

---

### Docker Container

![Docker Running](screenshots/docker-running.png)

---

### Docker Hub Repository

![Docker Hub](screenshots/dockerhub.png)

---

### EC2 Instance

![EC2](screenshots/ec2-instance.png)

---

## Useful Docker Commands

Build image

```bash
docker build -t docker-nodejs-app .
```

Run container

```bash
docker run -d -p 3000:3000 --name node-app docker-nodejs-app
```

List running containers

```bash
docker ps
```

View logs

```bash
docker logs node-app
```

Stop container

```bash
docker stop node-app
```

Start container

```bash
docker start node-app
```

Remove container

```bash
docker rm node-app
```

Remove image

```bash
docker rmi docker-nodejs-app
```

---

## Skills Demonstrated

- Cloud Computing (AWS EC2)
- Linux Administration
- Docker Containerization
- Node.js Deployment
- Networking and Security Groups
- Docker Hub Image Management
- Git & GitHub Version Control

---

## Future Improvements

- Deploy using Docker Compose
- Configure Nginx as a reverse proxy
- Add HTTPS using Let's Encrypt
- Implement CI/CD with GitHub Actions
- Deploy on Amazon ECS
- Monitor containers with CloudWatch

---

## Author

**Tevin Omondi**

- GitHub: https://github.com/tevinomondifreelance-design
- Docker Hub: https://hub.docker.com/u/tevinportfolio
- LinkedIn: *(Add your LinkedIn profile here)*

---

## License

This project is licensed under the MIT License.