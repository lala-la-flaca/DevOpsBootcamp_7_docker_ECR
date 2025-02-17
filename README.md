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
2. Create an admin user using IAM service.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/Creating%20Admin%20User%202.png" width=500 />
   
3. Assign admin privileges.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/providing%20administrator%20privileges.png" width=500 />

5. Sign out from the root user.
6. Sign in using the admin user account.
7. Create an access key pair.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/Adding%20access%20keys.png" width=500 />


### Create a private repository on Amazon ECR
1. Search for the ECR service in the search bar.
2. Click on Create a Repository.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/01%20CreatingAWS-ECR.png" width=500/>
   
4. In the repository name, enter the name of the application and save.
 
6. Follow the instructions from the link below to install AWS CLI.
   
   [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
   
8. Configure the AWS CLI to access AWS, using the access keys created in the previous section.

   ```bash
   aws configure
   ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/02%20Configuring%20Credentials%20to%20access%20CLI.png" width=500 />
   
9. Verify that the credentials were successfully created by navigating to the .aws directory and reviewing the credentials file.

   ```bash
   cd /.aws
   ls
   cat credentials
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/03%20To%20double%20check%20credentials.png" width=500 />


### Pushing Images to Amazon ECR

1. The commands to push to ECR are available under the push commands option when selecting the desired repository.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/04%20View%20push%20commands%20ECR.png" width=500 />

3. Retrieve an authentication token to access ECR using the following command:

    ```bash
    aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 734066168422.dkr.ecr.us-east-2.amazonaws.com
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/05%20push%20commands%20ECR%201.png" width=500 />
   
5. Tag the image to be able to push the image to ECR by using the docker tag command:

   ```bash
   docker tag js-app:1.0 734066168422.dkr.ecr.us-east-2.amazonaws.com/js-app:1.0
   ```
   
7. Push the image to ECR using the docker push command.

   ```bash
   docker push 734066168422.dkr.ecr.us-east-2.amazonaws.com/js-app:1.0
   ```

   ⚠️ **Note:**  - Ensure to change the latest tag to your current version, latest --> 1.0
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/05%20push%20commands%20ECR%202.png" width=500 />
   
9. Access the ECR to verify that the app images are available on AWS.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/06%20Image%20available%20in%20AWS-ECR.png" width=500 />
   
11. Modify the docker-compose.yml file to add a service for the application, and update the application code accordingly to ensure compatibility with the new service.

    <img src="<img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/10%20NewServerMongoYAMLFile2.png?raw=true" width=500 />
    
13. Remove the first version of the image 1.0
    
15. Build the new image using docker build and Dockerfile

     ```bash
     docker build -t js-app:1.0 .
    ```
    
16. Tag the New image

     ```bash
     docker tag js-app:1.0 734066168422.dkr.ecr.us-east-2.amazonaws.com/js-app:1.0
     
17. Push the new image to Amazon ECR using the docker push command:

    ```bash
     docker push 734066168422.dkr.ecr.us-east-2.amazonaws.com/js-app:1.0
    ```
    
    <img src=""/>

### Deploying the application
1. Access the new server.
2. Authenticate to Amazon ECR by running the following command:

   ```bash
   aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 734066168422.dkr.ecr.us-east-2.amazonaws.com
   ```
   
4. Create a YAML file and copy the content from the previous YAML file

   ```bash
   vim mongo.yaml
   ```
   
6. Run docker compose command.

   ```bash
   docker compose -f mongo.yaml up
   ```
     
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/11%20NewServerContainersUp.png" width=500 />

