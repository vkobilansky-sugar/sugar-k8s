# Sugar Kubernetes 
This repository will help you deploy a Kubernetes local enviornment. We'll be using `minikube` to simulate a Kubernetes cluser.

# Prerequisites 
You need to have `kubectl` and `minikube` installed on your local (host machine). Likewise `minikube` requires VirtualBox in order create a VM machine simulating the Kubernetes cluster.
Please ensure that you have all of these componentes in place before proceeding further. 

Check by running:
* `minikube version`
* `kubectl version`

# Getting started
* Start minikube: `minikube start --memory 8192`
* Start kubernetes stack:

```
cd <directory of cloned repo> (sugar-k8s by deafult)
kubectl apply -f stacks/sugar83/
```

This should bring up the entire stack required to run SugarCRM.
Now you can run `minikube dashboard` to review whether the componentes of the stack have started up as expected.
Likewise, you can run `minikube service list` to see different services, your output should look something like this:

```
|-------------|----------------------|-----------------------------|
|  NAMESPACE  |         NAME         |             URL             |
|-------------|----------------------|-----------------------------|
| default     | elasticsearch        | http://192.168.99.104:31457 |
| default     | kubernetes           | No node port                |
| default     | mysql-service        | No node port                |
| default     | sugar-redis          | No node port                |
| default     | web-service          | http://192.168.99.104:32740 |
| kube-system | kube-dns             | No node port                |
| kube-system | kubernetes-dashboard | No node port                |
|-------------|----------------------|-----------------------------|
```

Note that `web-service` is exposed via a local IP. This allows you to access your stack through the browser. You may `Cmd + click` on the IP (URL) in the table, or run `minikube service web-service` to bring up the index page of the application. 

# Installing SugarCRM 
* Download desired version of SugarCRM form Honeycomb
* Extract application files into `data/app/sugar` so that `index.php` and all relevant directories and sugar files are in the root of the `sugar` dirrectory. 
* Once you open the browser to the stack's IP (as described above), you should see the familiar SugarCRM installation wizard prompt. 