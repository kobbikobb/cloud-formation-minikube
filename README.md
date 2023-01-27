# Introduction

Run an EC2 instance with Minikube.
Deploy an application.
Expose Minikube with a reverse proxy.

The scripts will create resources in: us-east-1

## How to run it
- export AWS_PROFILE=user1 # The name of the profile you want to use
- ./create-stack.sh

## How to clean up
- ./delete-stack.sh

# Tips

## List profiles
aws configure list-profiles

## Select profile
export AWS_PROFILE=user1

## Make a sh file executable
sudo chmod +x filename.bin

## List all volumes on a machine
lsblk

# EC2 errors for UserData
sudo cat /var/log/cloud-init-output.log