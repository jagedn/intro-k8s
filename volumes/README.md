# Volumes

Requires to create a new cluster

`k3d cluster delete lab`

`k3d cluster create lab --port 9999:80@loadbalancer --volume /tmp/k3dvol:/tmp/k3dvol --registry-use k3d-lab-registry.localhost:38701`