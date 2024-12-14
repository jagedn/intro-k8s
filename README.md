# Intro Kubernetes

# requirements

- Linux
- Docker installed

# kubectl

`curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"`

# k9s

https://github.com/derailed/k9s/releases

# k3d

`curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash`

`k3d cluster create lab --port 9999:80@loadbalancer --registry-create lab-registry`

`docker ps` # find the registry port

`k9s`

# Kube config

`cat $HOME/.kube/config`

```
apiVersion: v1

clusters:
- cluster:
    ....
users:
- name: admin@k3d-lab
  user:
    client-certificate-data: ......

contexts:    
- context:
    cluster: k3d-lab
    user: admin@k3d-lab
  name: k3d-lab
current-context: k3d-lab
```

# Pod -> Deployment -> Service -> Ingress

# ConfigMap vs Secret

# Hello wolrd

cd hello-world

docker build -t hello-world .

docker tag hello-world:latest lab-registry.localhost:38701/hello-world

docker push lab-registry.localhost:38701/hello-world

## Pods & Deployment

kubectl apply -f deployment.yml

port-forward 8080:80


## Service

kubectl apply -f service.yml

## ConfigMaps (vs Secrets)

kubectl apply -f configmap.yaml

kubectl apply -f deployment-config.yml


## Clean all

kubectl delete -f deployment-config.yml -f configmap.yml -f service.yml -f traefik.yml

k3d cluster delete lab

## TODO

PersistentVolume + PersistentVolumeClaim