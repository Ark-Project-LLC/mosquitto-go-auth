# Mosquitto-go-auth for Ark Project

This repo is a fork from https://github.com/iegomez/mosquitto-go-auth repository.
There are few changes in the repo:

1. Install gettext

There is a change to the `Dockerfile` which will install the `gettext` package. The `envsubst` command will be used to do some environment variables replacement before running mosquitto in the Arkproject setting.

2. This md file

In this file there is a brief description of changes to the forked repo.

## Build the image and deploy to the AWS ECR repository

```shell
docker build -t 277058424174.dkr.ecr.us-east-2.amazonaws.com/mosquitto-go-auth:2.1.0 .
docker tag 277058424174.dkr.ecr.us-east-2.amazonaws.com/mosquitto-go-auth:2.1.0 277058424174.dkr.ecr.us-east-2.amazonaws.com/mosquitto-go-auth:latest
```

Run the docker login command:

```shell
aws ecr get-login-password --region us-east-2 --profile arkproject-ecr-full | docker login --username AWS --password-stdin 277058424174.dkr.ecr.us-east-2.amazonaws.com
```

Be sure to create the `arkproject-ecr-full` profile in your aws configuration and config files and populate with proper values.

Now push the images to the AWS ECR:

```shell
docker push 277058424174.dkr.ecr.us-east-2.amazonaws.com/mosquitto-go-auth:2.1.0
docker push 277058424174.dkr.ecr.us-east-2.amazonaws.com/mosquitto-go-auth:latest
```
