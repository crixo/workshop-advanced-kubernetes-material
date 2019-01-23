# Prometheus configuration and recording rules

This folder conatins Kubernetes manifests to deploy a Prometheus configuration
to enable service discovery under Kubernetes and example recording rule to
record CPU utilisation from `node_exporter`.

To deploy these manifests run the following command
```shell
$ kustomize build . | kubectl apply -f -
```

## Exercise: define your own recording rules


