# Sample Kubernetes Deployment

Sample Kubernetes scripts to deploy Ghost blog to a Kubernetes cluster in local
Deployment structure:

```
ghost-svc -> ghost-deploy (3 pods) -> mysql-svc -> mysql-deploy (1 pod)
```

## Deploy using Kubernetes Deployments to local cluster

1. Create `mysql` deployment: `kubectl apply -f mysql-deployment.yml`
2. Create `mysql-svc` ClusterIP service so that it's accessible by `ghost` application: `kubectl apply -f mysql-service.yml`
3. Create `ghost` deployment: `kubectl apply -f ghost-deployment.yml`
4. Create `ghost-svc` NodePort service so that it's accessible by external clients: `kubectl apply -f ghost-service.yml`

Ghost application can be accessed from: http://localhost:30001

**The same deployments can be applied to GKE**, but in order to make the cluster available to public, need to create additional ingress, pointing to `ghost-svc`:

```
kubectl apply -f ghost-ingress.yml
```

The service can be accessed through ingress public IP, port 80

## Deploy using Kubernetes ReplicaSets

For testing only. Deploying using Kubernetes Deployment is preferred. This will create a ReplicaSet with multi-containers in a pod

```
kubectl apply -f ghost-rs.yml
```

## Run using docker-compose

`docker-compose.yml` is docker compose equivalent of this setup
