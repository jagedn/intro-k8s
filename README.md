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

# Docker registry

`k3d registry create lab-registry.localhost --port 38701`

test the registry

```
docker pull hello-world
docker image tag hello-world k3d-lab-registry.localhost:38701/docker-hello
docker push k3d-lab-registry.localhost:38701/docker-hello
docker run -rm -it k3d-lab-registry.localhost:38701/docker-hello
``` 

# Our cluster

`k3d cluster create lab --port 9999:80@loadbalancer --registry-use k3d-lab-registry.localhost:38701`


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


# 1. Hello world

follow hellow-world/README.md

# 2. ConfigMap

follow config-maps/README.md

# 3. Secrets

follow secrets/README.md

# 4. Volumes

follow volumes/README.md

## Clean all

kubectl delete -f deployment-config.yml -f configmap.yml -f service.yml -f traefik.yml

k3d cluster delete lab

