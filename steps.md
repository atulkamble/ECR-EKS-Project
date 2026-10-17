```
// EKS Cluster Creation 

eksctl create cluster --name mycluster --region us-east-1 --nodegroup-name mynodes --node-type t3.medium --nodes 2 --nodes-min 2 --nodes-max 2 --managed

OR 

eksctl create cluster --name mycluster --region us-east-1 --node-type t3.small --nodes 2 --nodes-min 2 --nodes-max 2 --with-oidc --managed

aws eks update-kubeconfig --name mycluster --region us-east-1

kubectl get nodes 

// Clone Git Code and Build Docker Image and test it
// Docker Desktop running in background 

git clone https://github.com/atulkamble/ECR-EKS-Project.git
cd ECR-EKS-Project
cd code 
pwd 

git pull
docker buildx build -t myapp .
docker images
docker run -d -p 80:80 myapp:latest

http://localhost 

docker container ls
docker container stop 3da4a7b5531e
docker container start 3da4a7b5531e

// ECR 

aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 535002879962.dkr.ecr.us-east-1.amazonaws.com

docker buildx build --platform linux/amd64,linux/arm64 -t 535002879962.dkr.ecr.us-east-1.amazonaws.com/cloudnautic/myapp:latest --push .

kubectl apply -f deployment.yaml 
kubectl apply -f service.yaml

kubectl get pods
kubectl get svc 

kubectl describe pod pod-id 
kubectl describe service service-name 
```


