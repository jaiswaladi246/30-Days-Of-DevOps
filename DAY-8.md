# DAY-8 | DOCKER WITH JENKINS
Docker is an open-source platform that allows you to automate the deployment, scaling, and management of applications using containerization. Containers provide a lightweight and portable way to package applications and their dependencies, enabling them to run consistently across different environments.
Sure! Here's the provided content converted into a GitHub README.md format:


# Real-World Scenario: Development and Deployment of a Web Application using Docker

In this scenario, a team of developers is working on a web application that consists of multiple microservices. They want to ensure consistent and reliable development, testing, and deployment processes across different environments.

## 1. Development Environment

- Each developer sets up their local development environment using Docker. They can use Docker Compose to define the services required for the application, such as web server, database, cache, etc.
- Docker containers allow developers to work with consistent and isolated environments. They can easily share the Docker Compose configuration, ensuring everyone has the same setup.

## 2. Continuous Integration (CI)

- The team uses a CI/CD pipeline for automated testing and deployment. Docker can be utilized in the CI process to create reproducible build environments.
- The CI system can build Docker images based on the application code, using a Dockerfile.
- The Docker images can be tagged with a unique identifier, such as the commit hash or build number.

## 3. Testing Environment

- Docker makes it easy to set up and tear down testing environments. The CI system can spin up Docker containers based on the built images and run automated tests against the application.
- Different testing environments, such as staging or integration, can be created using separate Docker Compose configurations.
- Containers can be quickly provisioned and isolated, allowing for parallel testing and efficient resource utilization.

## 4. Deployment

- The tested and validated Docker images can be pushed to a Docker registry, making them available for deployment.
- The deployment environment, such as production or a cloud-based infrastructure, can use Docker to provision and manage containers.
- Docker orchestration tools like Docker Swarm or Kubernetes can be used for container orchestration, scaling, and high availability.

Benefits of Using Docker in this Scenario:

- Consistency: Docker ensures consistent environments across different stages of development, testing, and deployment, reducing issues related to environment inconsistencies.
- Reproducibility: Docker allows the creation of reproducible build environments, ensuring that the application runs the same way in different environments.
- Scalability: Docker's containerization enables easy scaling of services and efficient resource utilization.
- Isolation: Containers provide process isolation, preventing conflicts between different services or dependencies.
- Portability: Docker containers can be run on different platforms and cloud providers, facilitating seamless deployment and migration.

This is just one example of how Docker can be used in a real-world scenario. Docker's flexibility and efficiency make it a popular choice for many development and deployment workflows, regardless of the specific application or infrastructure requirements.


# Docker Commands to build, tag, push and run a docker image

To build, tag, push, and run a Docker image, you can use the following Docker commands:

## 1. Build an Image

```
docker build -t <image_name> <path_to_dockerfile>
```

This command builds a Docker image using the Dockerfile located at `<path_to_dockerfile>`. The `-t` flag is used to provide a name or tag to the image.

## 2. Tag an Image

```
docker tag <image_name> <new_tag>
```

This command assigns a new tag to an existing Docker image. The `<image_name>` is the name or ID of the image you want to tag, and `<new_tag>` is the new tag you want to assign.

## 3. Push an Image to a Docker Registry

```
docker push <image_name>
```

This command pushes a Docker image to a Docker registry, making it available for others to download and use. The `<image_name>` is the name or tag of the image you want to push.

Note: Before pushing an image, you may need to log in to the Docker registry using the `docker login` command and providing your credentials.

## 4. Run a Docker Image

```
docker run <image_name>
```

This command runs a Docker image as a container. The `<image_name>` is the name or tag of the image you want to run. Additional flags and options can be used to customize the container's behavior, such as specifying ports, volumes, environment variables, etc.

For example, to run a container and map a local port to a container port, you can use the `-p` flag:

```
docker run -p <host_port>:<container_port> <image_name>
```

These commands assume that you have Docker installed and configured on your system. They are meant to provide a general overview, and there are many more advanced options and configurations available for Docker. I recommend consulting the [official Docker documentation](https://docs.docker.com/) for more details and examples specific to your use case.


## Jenkins Declarative Pipeline script:

```groovy
pipeline {
    agent any
    
    tools {
        jdk 'jdk11'
        maven 'maven3'
    }
    
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }
    
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/jaiswaladi246/Shopping-Cart.git'
            }
        }
        
        stage('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }
        
        stage('Sonarqube Analysis') {
            steps {
                sh '''
                    $SCANNER_HOME/bin/sonar-scanner \
                    -Dsonar.url=http://13.233.102.184:9000/ \
                    -Dsonar.login=squ_815b4e28b618be7ab62693da256718391e4046d3 \
                    -Dsonar.projectName=Shopping-Cart \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=Shopping-Cart
                '''
            }
        }
        
        stage('Build') {
            steps {
                sh "mvn clean package -DskipTests=true"
            }
        }
        
        stage('OWASP Dependency Check') {
            steps {
                dependencyCheck additionalArguments: '--scan target/', odcInstallation: 'owasp'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'c9b058e5-bfe6-41f8-9b5d-dc0b0d2955ac', toolName: 'docker') {
                        sh "docker build -t shopping-cart -f docker/Dockerfile ."
                        sh "docker tag shopping-cart adijaiswal/shopping-cart:latest"
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'c9b058e5-bfe6-41f8-9b5d-dc0b0d2955ac', toolName: 'docker') {
                        sh "docker push adijaiswal/shopping-cart:latest"
                    }
                }
            }
        }
        
        stage('Deploy To Docker Container') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'c9b058e5-bfe6-41f8-9b5d-dc0b0d2955ac', toolName: 'docker') {
                        sh "docker run -d --name shopping -p 8070:8070 adijaiswal/shopping-cart:latest"
                    }
                }
            }
        }
    }
}
```

![alt text](https://github.com/jaiswaladi246/30-Days-Of-DevOps/blob/main/Images/6.png?raw=true)

## Deployed Application
![alt text](https://github.com/jaiswaladi246/30-Days-Of-DevOps/blob/main/Images/7.png?raw=true)
