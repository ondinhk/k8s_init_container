# Deploy hello java app using k8s without docker build command
## Note: Using initcontainer in Deployment for build docker image

## Build source code
```bash
./hello-java-app/mvnw clean install
```

## Use this command for start k8s and mount this dir to volume vitural cluster
```bash
minikube start --mount=true --mount-string=$(pwd):/mnt/data
```
## Waiting minikube start and run this command
```bash
kubectl apply -f volume.yaml
kubectl apply -f volume-claim.yaml
kubectl apply -f deployment.yml
kubectl apply -f service.yml
```
## Flow
Create volume -> create volume claim -> create deployment -> create service

## How to test
```bash
curl 192.168.49.2:30041/hello
```
