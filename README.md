# netbox-kubernetes

Kubernetes manifest resources for Netbox.  
All images are pulled from docker hub.  
Netbox images pulled from the [community-maintained Docker Hub](https://hub.docker.com/r/netboxcommunity/netbox/).

# Quickstart on Minikube

To get NetBox up and running on Minikube:

```
$ git clone
$ cd netbox-kubernetes
$ kubectl apply -f netbox-pvc.yaml
$ kubectl apply -f netbox-env-configmap.yaml
$ kubectl apply -f netbox-deployment.yaml
```

At the moment you can access the application using follwing command.

```
$ kubectl get pods -n netbox
```

Now you can replace "Nginx-Pod-Name":

```
$ kubectl port-forward Nginx-Pod-Name 8001:80 --namespace netbox
```

**8001 is a localport** It can be changed according to you.
The application will be available after a few minutes.
"http://localhost:8001"

```
**accessing** Netbox using NodePort
As Netbox is using ALLOWED_HOST variable, we need to update the value of it as well as in /etc/hosts in order to access it on nodeport. for example, netbox.netbox is FQDN   
"http://netbox.netbox:NODEPORT"
```

Default credentials:

* Username: **admin**
* Password: **admin**
* API Token: **0123456789abcdef0123456789abcdef01234567**

# Dependencies

https://hub.docker.com/r/netboxcommunity/netbox/

# Road Map/To Do

* Ingress-Controller
* Helm Chart

# About

This is a living document.  
If you spot areas that can be improved or rewritten, contributions are welcome!
