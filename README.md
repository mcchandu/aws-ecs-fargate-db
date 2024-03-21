# aws-ecs-fargate
Scalable Web Server Based on AWS ECS and Fargate services

## Requirements
 - Terraform v1.7.5
 - provider registry.terraform.io/hashicorp/aws v5.41.0
 - Nodejs v20

## Build and publish docker image
### Requirements
 - Specified `DOCKER_HUB_ACCESS_TOKEN` secret in GitHub repository secrets. The token is should be taken from your DockerHub account.
 - Specified `DOCKER_HUB_USERNAME` variable in GitHub repository variables. The username is should be taken from your DockerHub account.
 - The `DATABASE_CONNECTION_URI` could be with any default value, the prod value will be generated by terraform on apply stage.
 - The `REDIS_HOST` could be with any default value, the prod value will be generated by terraform on apply stage.

### Instructions
The build and publish docker image the process is automatically initiated on package version bump triggered by running `npm run version:patch` or `yarn version:patch` from the repo root folder.

## Terraform deployment
### Requirements
 - Created AWS account
 - Created user with admin rights and downloaded AWS access key for this user `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`
 - The `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` should be stored in the GitHub secrets

### Instructions
 - Create any pull request in GutHub
 - Comment in pull request `/plan prod`, where `/plan` is the action for terraform and `prod` in workspace
 - Check GitHub actions and in case no issues detected proceed with the next step
 - Comment in pull request `/apply prod`, where `/apply` is the action for terraform and `prod` in workspace
 - Check GitHub action result for errors

