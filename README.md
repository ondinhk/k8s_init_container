# Build source code
./hello-java-app/mvnw clean install

# Use this command for start k8sand mount this dir to volume vitural cluster
minikube start --mount=true --mount-string=$(pwd):/mnt/data

# Waiting minikube start and run this command
kubectl apply -f volume.yaml
kubectl apply -f volume-claim.yaml
kubectl apply -f deployment.yml
kubectl apply -f service.yml

# Flow
Create volume -> create volume claim -> create deployment -> create service

# How to test
curl 192.168.49.2:30041/hello
