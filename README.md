# Containers with Docker 🐳 and Amazon ECR
This demo project is part of Module 7: Containers with Docker from the Nana DevOps Bootcamp and focuses on the fundamentals of containerization with MongoDB and Mongo-Express. It covers building a Docker image using a Dockerfile, creating a Docker registry on AWS with Amazon ECR, pushing Docker images to Amazon ECR, and running containers on a newly provisioned server. This hands-on project provides a practical foundation for managing and deploying containerized applications using Docker.

## 🚀 Technologies Used

- <b>Docker for containerization.</b>
- <b>Mongo DB: Serves as a database to persist NodeJS data.</b>
- <b>Mongo-Express: WebUI access for managing Mongo DB.</b>
- <b>Linux: Ubuntu for Server configuration and management.</b>
- <b>NodeJs/npm: Nana's application from DevOps Bootcamp and package manager.</b>
- <b>Amazon ECR: Container registry to store docker images on AWS.</b>


## 🎯 Features

- <b>Create Dockerfile.</b>
- <b>Install AWS CLI.<b>
- <b>Create an AWS account using admin user.<b>
- <b>Create private registry on AWS.</b>
- <b>Push docker images to ECR.</b>
- <b>Deploy nodeJS application on a fresh server.</b>


## 🏗 Project Architecture

<img src=""/>

## ⚙️ Project Configuration:

### Create Dockerfile
1. Use the Dockerfile image that was created in the previous demo.

### Create an AWS account
1. Create an AWS account using a root user.
2. Create an admin user using IAM and assign admin privileges.
4. Sign out from the root user.
5. Sign in using the admin user account.
6. Create an access key pair.


### Create a private repository on Amazon ECR
1. Search ECR service on the search bar.
2. Click on Create Registry.
3. On the repository name assign the name of the app, in this case js-app.
4. Configure the console to access AWS with the access keys created in the previous section.
5. Double-check that the credentials were successfully created by accessing the .aws directory and check the credentials file.

### Pushing Images to Amazon ECR
1. The commands to push to ECR are available under the push commands option when selecting the desired repository.
2. Retrieve an authentication token to access ECR.
3. Tag the image to be able to push the image to ECR.
4. Push the image to ECR.
5. Access the ECR to verify that the app images are available on AWS.
6. Modify the image to add the service for the app in the docker-compose file and modify the application accordingly.
7. Push new image to Amazon ECR.

### Deploying the application
1. Access the new server.
2. Authenticate to Amazon ECR
3. Create the YAML file.
4. Run docker compose command.

