# Sugar Kubernetes 
This repository will help you deploy a Kubernetes based local enviornment. We'll be using `minikube` to simulate a Kubernetes cluser on local.

# Prerequisites 
You need to have `kubectl` and `minikube` installed on your local. `minikube` requires VirtualBox in order create a VM machine simulating the Kubernetes cluster.
Please ensure you have all of these componentes in place before proceeding further. 

Check by running:
* `minikube version`
* `kubectl version`

# Getting started
* Start minikube: `minikube start --memory 8192`
* Start kubernetes stack:
```
cd <directory of cloned repo> (sugar-k8s by deaful)
kubectl apply -f stacks/sugar83/
```

This should bring up the entire stack required to run SugarCRM.
Now you can run `minikube dashboard` to review whether the componentes of the stack have started up as expected.
Likewise, you can run `minikube service list` to see different services, your output should look something like this:
```
|-------------|----------------------|-----------------------------|
|  NAMESPACE  |         NAME         |             URL             |
|-------------|----------------------|-----------------------------|
| default     | kubernetes           | No node port                |
| default     | mysql-service        | No node port                |
| default     | redis-master         | No node port                |
| default     | redis-slave          | No node port                |
| default     | web1-service         | http://192.168.99.103:31594 |
| kube-system | kube-dns             | No node port                |
| kube-system | kubernetes-dashboard | No node port                |
|-------------|----------------------|-----------------------------|
```

Note that `web1-service` is exposed via a local IP. This allows you to access your stack through the browser. You may `Cmd + click` on the IP (URL) in the table, or run `minikube service web1-service` to bring up the index page of the application. 