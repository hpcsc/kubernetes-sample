# Sample Kubernetes Deployment

Sample Kubernetes scripts to deploy Ghost blog to a Kubernetes cluster in local

## Deploy using Kubernetes Deployments

```
kubectl create -f ghost-deployment.yml
```

## Deploy using Kubernetes ReplicaSets

```
kubectl create -f ghost-rs.yml
```

## Create Kubernetes Service to access pods

```
kubectl create -f ghost-service.yml
```

Access by: http://localhost:30001
