# Containerize, Deploy, and Automate a Microservices TODO Application

## Detailed Project Task
https://github.com/jubriledun/jubriledun_devops-stage4/blob/main/Question.txt

## Project Overview
This project involves containerizing a microservices TODO application and automating its deployment using Infrastructure as Code (IaC). The application consists of a Vue.js frontend, multiple backend services (Go, Node.js, Java, Python), and a Redis queue, all containerized using Docker and managed with Docker Compose. Infrastructure provisioning and configuration will be automated using Terraform and Ansible to deploy the application seamlessly on the cloud. The final setup will enable one-command deployment (terraform apply -auto-approve), ensuring a fully automated and scalable deployment process.

## Project Objectives
For this project, the following objectives were achieved;

Containerization: each microservice was packaged into Docker containers with optimized Dockerfiles.
Simplified Deployment: Docker Compose was used to orchestrate multi-container deployment with a single command (docker-compose up -d).
Infrastructure Automation: Terraform was utilized to provision cloud infrastructure and manage security configurations dynamically.
Configuration Management: Server setup and application deployment was automated using Ansible.
Domain Setup: Custom domain was configured using namecheap.

The app itself is a simple TODO app that additionally authenticates users.

## Components

1. [Frontend](/frontend) part is a Javascript application, provides UI. Created with [VueJS](http://vuejs.org)
2. [Auth API](/auth-api) is written in Go and provides authorization functionality. Generates JWT tokens to be used with other APIs.
3. [TODOs API](/todos-api) is written with NodeJS, provides CRUD functionality ove user's todo records. Also, it logs "create" and "delete" operations to Redis queue, so they can be later processed by [Log Message Processor](/log-message-processor).
4. [Users API](/users-api) is a Spring Boot project written in Java. Provides user profiles. Does not provide full CRUD for simplicity, just getting a single user and all users.
5. [Log Message Processor](/log-message-processor) is a very short queue processor written in Python. It's sole purpose is to read messages from Redis queue and print them to stdout


The diagram describes the various components and their interactions.
![microservice-app-example](https://user-images.githubusercontent.com/1905821/34918427-a931d84e-f952-11e7-85a0-ace34a2e8edb.png)

Note: 3 different login details are provided in the .env file 




## Buying the Domain mane
![image](https://github.com/user-attachments/assets/8ead64c8-684b-49c2-b5e0-5a14036227e6) <br> <br>

