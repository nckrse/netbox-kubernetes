# netbox-kubernetes

Kubernetes manifest resources for Netbox.  
All images are pulled from docker hub.  
Netbox images pulled from the [community-maintained Docker Hub](https://hub.docker.com/r/netboxcommunity/netbox/).

# Quickstart on MicroK8s

> Note: DNS and Ingress addons must be enabled (`microk8s status`)

To get NetBox up and running on MicroK8s:

```
$ git clone
$ cd netbox-kubernetes
$ kubectl apply -f netbox-namespace.yaml
$ kubectl apply -f netbox-pvc.yaml
$ kubectl apply -f netbox-env-configmap.yaml
$ kubectl apply -f netbox-deployment.yaml
$ kubectl apply -f netbox-secrets.yaml
$ kubectl apply -f netbox-microk8s-ingress.yaml
```

At the moment you can validate the pods status using following command.

```
$ kubectl get pods -n netbox
```

The application will be available after a few minutes:

[http://microk8s_ip/](null)


Default credentials:

* Username: **admin**
* Password: **admin**
* API Token: **0123456789abcdef0123456789abcdef01234567**

# Dependencies

https://hub.docker.com/r/netboxcommunity/netbox/

# Road Map/To Do

* Helm Chart

# About

* Modify `netbox-pvc.yaml` with your NFS server/path or alternate storage (Ceph, etc.)
* Modify `netbox-secrets.yaml` with your secrets (must be base64 encoded). NAPALM and Email are null and Kubernetes doesn't support null base64 values, so these remain in `netbox-env-configmap.yaml` until changed
* Modify `netbox-microk8s-ingress.yaml` if you would rather support a host-based configuration instead of catchall

_This is a living document._
_If you spot areas that can be improved or rewritten, contributions are welcome!_
