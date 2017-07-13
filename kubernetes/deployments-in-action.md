# Pods, ReplicaSets, Deployments

Now you should know all the theory behind `Pods`, `ReplicaSets`, `ReplicationControllers` and `Deployments` but **what are they**?

here is a simple example of `Deployment`:

```yaml
apiVersion: apps/v1beta1 # Version of the Kubernetes API to use, necessary for kubectl
kind: Deployment
metadata:
  name: nginx-deployment # Name referenced during the deployment life
spec:
  replicas: 3 # Desired state ensured by rs
  template:
    metadata:
      labels: # Labels (simple key-values) associated with the pod
        app: nginx
    spec:
      containers: # The actual containers, a simple nginx exposing port 80
      - name: nginx
        image: nginx:1.7.9
        ports:
        - containerPort: 80
```

# Let's play a bit

Let's define a baseline: we will issue all our commands from `$PROJECT_HOME/kubernetes`

First of all, let's see the current state of our cluster:

```bash
kubectl get nodes

NAME       STATUS    AGE       VERSION
minikube   Ready     1d        v1.6.4
```

```bash
kubectl get pods

No resources found
```

So, we have a clean cluster!

Let's create our first deployment.

```bash

kubectl create -f deployments/nginx-deployment.yaml

kubectl get pods

NAME                                READY     STATUS    RESTARTS   AGE
nginx-deployment-4234284026-02j4d   1/1       Running   0          28s
nginx-deployment-4234284026-267f6   1/1       Running   0          28s
nginx-deployment-4234284026-g9819   1/1       Running   0          28s
```
