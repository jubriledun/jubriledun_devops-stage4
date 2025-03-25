# Containerize, Deploy, and Automate a Microservices TODO Application

## Detailed Project Task
https://github.com/jubriledun/jubriledun_devops-stage4/blob/main/Question.txt

## Project Overview
This project involves containerizing a microservices TODO application and automating its deployment using Infrastructure as Code (IaC). The application consists of a Vue.js frontend, multiple backend services (Go, Node.js, Java, Python), and a Redis queue, all containerized using Docker and managed with Docker Compose. Infrastructure provisioning and configuration will be automated using Terraform and Ansible to deploy the application seamlessly on the cloud. The final setup will enable one-command deployment (terraform apply -auto-approve), ensuring a fully automated and scalable deployment process.

## Project Objectives
For this project, the following objectives were achieved;

- Containerization: each microservice was packaged into Docker containers with optimized Dockerfiles.
- Simplified Deployment: Docker Compose was used to orchestrate multi-container deployment with a single command (docker-compose up -d).
- Infrastructure Automation: Terraform was utilized to provision cloud infrastructure and manage security configurations dynamically.
- Configuration Management: Server setup and application deployment was automated using Ansible.
- Domain Setup: Custom domain was configured using namecheap.

## Application Components

1. [Frontend](/frontend) part is a Javascript application, provides UI. Created with [VueJS](http://vuejs.org)
2. [Auth API](/auth-api) is written in Go and provides authorization functionality. Generates JWT tokens to be used with other APIs.
3. [TODOs API](/todos-api) is written with NodeJS, provides CRUD functionality ove user's todo records. Also, it logs "create" and "delete" operations to Redis queue, so they can be later processed by [Log Message Processor](/log-message-processor).
4. [Users API](/users-api) is a Spring Boot project written in Java. Provides user profiles. Does not provide full CRUD for simplicity, just getting a single user and all users.
5. [Log Message Processor](/log-message-processor) is a very short queue processor written in Python. It's sole purpose is to read messages from Redis queue and print them to stdout


The diagram describes the various components and their interactions.
![microservice-app-example](https://user-images.githubusercontent.com/1905821/34918427-a931d84e-f952-11e7-85a0-ace34a2e8edb.png)

Note: 3 different login details are provided in the .env file 


## Project Implementation

### Dockerizing the microservices
- Dockerfile for Frontend service
  ![image](https://github.com/user-attachments/assets/7d209343-5210-406d-816a-939d55c341d2)
  
- Dockerfile for Auth API service
  ![image](https://github.com/user-attachments/assets/08caf2da-cd7a-46af-8457-483d6587c910)

- Dockerfile for Todos API service
  ![image](https://github.com/user-attachments/assets/1624e4cf-ba25-4fc8-a5d3-8cd7d994ca56)

- Dockerfile for Users API service
  ![image](https://github.com/user-attachments/assets/21930174-57c5-4d57-996d-c1d6075e761d)

- Dockerfile for Log Message Processor service
  ![image](https://github.com/user-attachments/assets/d7b020e3-1a67-4461-b20d-7f921d445572)

- Nginx config for frontend service to serve as reverse proxy
  ![image](https://github.com/user-attachments/assets/38b13560-3863-47ac-b47b-15446ba6d174)


### Simplified Deployment (Docker compose)
- Link to docker compose file
  https://github.com/jubriledun/jubriledun_devops-stage4/blob/main/compose.yml


### Configuration Management with Ansible
- Playbook
  ![image](https://github.com/user-attachments/assets/69c16ffe-42c2-4a86-8a1e-23c34ec1c5f6)

- Dependencies role
  ![image](https://github.com/user-attachments/assets/def4797e-247a-449f-b76e-85a8ef8fe394)

- Deployment role
  ![image](https://github.com/user-attachments/assets/9db923d4-c9db-4af5-a0ed-1c7011442079)


### Infrastructure Automation with Terraform
### Setup AWS CLI Credentials
![image](https://github.com/user-attachments/assets/638335e3-93b5-46a0-8689-2dfadbe2d551)

- main.tf file
  ![image](https://github.com/user-attachments/assets/86ca579d-20ac-4975-8d94-dc2aa8174930)

- providers.tf file
  ![image](https://github.com/user-attachments/assets/0c92b040-19e3-4b7b-8c23-7c6c0b858c97)

- output.tf file
  ![image](https://github.com/user-attachments/assets/96e00585-3f25-48ad-9dd6-d2eac254eed9)

### Repo Link for Infrastructure provisioning
https://github.com/jubriledun/jubriledun_devops_stage4_infra

### Runing Terraform apply command
![image](https://github.com/user-attachments/assets/831773ad-affa-44de-a92c-75e30943e936)

![image](https://github.com/user-attachments/assets/434b51f4-0317-4ac4-8af9-e8edf8868f8c)


### Confirm application is running
![image](https://github.com/user-attachments/assets/0a52412c-1701-470a-8fa1-af3be2c2aa72)
![image](https://github.com/user-attachments/assets/49089cda-3c3c-4ed9-9a75-e19311e9e235)
![image](https://github.com/user-attachments/assets/8e0f60d5-c60d-42c3-8be0-7e3ee90a4df7)
![image](https://github.com/user-attachments/assets/1f2881a2-78b4-48d7-8e6e-12f89f708a1d)
![image](https://github.com/user-attachments/assets/79aa6c3b-31d7-460b-beac-dc46ff53cf1f)  

### Configuring Domain

### Buying the Domain mane
![image](https://github.com/user-attachments/assets/8ead64c8-684b-49c2-b5e0-5a14036227e6) 

### Updating DNS Records
![image](https://github.com/user-attachments/assets/25b92092-2266-410d-9f76-3521d51b1e1d)

### Confirm DNS works
![image](https://github.com/user-attachments/assets/80903714-702b-4cea-9f0b-ca5592fd3d45)
![image](https://github.com/user-attachments/assets/0479e63d-7b1e-4666-b2b6-2d3d581feeee)
![image](https://github.com/user-attachments/assets/d3edddad-7332-4d78-aab1-af0a375684c9)
![image](https://github.com/user-attachments/assets/36fa3f4e-f74d-4a00-ad8e-c72c82372dd8)
![image](https://github.com/user-attachments/assets/87f5318f-e9f0-4a1c-8b42-874bfd7203e3)

