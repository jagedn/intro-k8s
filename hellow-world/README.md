
# Hello wolrd

## Build and publish our application

```
cd nginx
docker build -t k3d-lab-registry.localhost:38701/hello-world .  #pay attention to the dot
docker push k3d-lab-registry.localhost:38701/hello-world
```

## Pods & Deployment

kubectl apply -f deployment.yml

port-forward 8080:80


## Service

kubectl apply -f service.yml

## Ingress (Traefik)

kubectl apply -f traefik.yml


## Testing

http://localhost:8080
