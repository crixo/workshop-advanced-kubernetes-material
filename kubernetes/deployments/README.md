# Pods, ReplicaSets, Deployments

Now you should know all the theory behind `Pods`, `ReplicaSets`, `ReplicationControllers` and `Deployments` but **what are they**?

here is a simple example of `Deployment`:

```yaml
apiVersion: apps/v1beta1 # for versions before 1.6.0 use extensions/v1beta1
kind: Deployment
metadata:
  name: nginx-deployment # name referenced by Kubernetes during the deployment lifecycle
spec:
  replicas: 3 # here is the desired state ensured by the ReplicaSet
  template:
    metadata:
      labels: # here are labels (simple key-values) associated with the pod
        app: nginx # labels attach
    spec:
      containers: # the actual containers, a simple nginx exposing port 80
      - name: nginx
        image: nginx:1.7.9
        ports:
        - containerPort: 80
```
