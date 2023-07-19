# Step-by-Step how to create an image until it will be deployed to AWS ECR

## Set up AWS Credentials:
### Ensure that you have an AWS account and the necessary credentials (Access Key ID and Secret Access Key) to interact with AWS services programmatically. 

## Install Docker
### Make sure you have Docker installed on your local machine. Docker will be used to build the container image.

## Write Dockerfile:
### Create a Dockerfile in the root directory of your application. The Dockerfile contains instructions to build the Docker image. It specifies the base image, dependencies, environment variables, and other configurations for the container.

## Build the Docker Image:
### Open a terminal, navigate to the directory containing the Dockerfile, and run the following command to build the Docker image:
#### docker build -t your-image-name:tag .
### Replace your-image-name with the desired name for your image and tag with a version or label for the image.

## Tag the Docker Image:
### Before pushing the image to ECR, you need to tag it with the ECR repository URI. Retrieve the ECR repository URI by running the following AWS CLI command:
#### aws ecr get-login-password --region your-region | docker login --username AWS --password-stdin your-account-id.dkr.ecr.your-region.amazonaws.com
### Replace your-region with the AWS region where your ECR repository is located and your-account-id with your AWS account ID.

## Push the Docker Image to ECR:
### Tag the Docker image using the ECR repository URI: 
#### docker tag your-image-name:tag your-account-id.dkr.ecr.your-region.amazonaws.com/your-repository-name:tag
### Replace your-repository-name with the name of your ECR repository.
### Now, push the Docker image to ECR:
#### docker push your-account-id.dkr.ecr.your-region.amazonaws.com/your-repository-name:tag

## Verify the Image in ECR:
### Go to the AWS Management Console, navigate to the ECR service, and select your repository. You should see the pushed image with the appropriate tag.













