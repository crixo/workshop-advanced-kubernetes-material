# Monitoring with Prometheus

This folder contains Kubernetes manifests to deploy a full monitoring stack
composed by Prometheus, Alertmanager, Grafana and node-exporter in the
`monitoring` namespace.

It is worth to point out that `node-exporter` is a pod of type `DaemonSet`,
meaning that kubernetes will make sure that exactly one `node-exporter` is ran
at all times on each node.

This is also a very concrete example of usage for `ConfigMaps` as we use them to
store Prometheus, Alertmanager and Grafana configuration files, the configmap
are then mounted as a `volume` and the configurations are made available to
the pods as a mounted file.

## Prometheus

The `prometheus` deployment is already configured to perform target discovery
through the Kubernetes API. Setting the annotation `prometheus.io/scrape` to
`true` on a `Service` object will be enough to have it appears under Prometheus
scrape targets. See [node-exporter.yaml](node-exporter.yaml) for an example.

The `prometheus` service is of type `NodePort`, therefore you can access it on
port `30990` like the following
```shell
$ IP=$(minikube ip)
$ curl http://${IP}:30990/-/ready
Prometheus is Ready.
$ curl http://${IP}:30990/-/healthy
Prometheus is Healthy.
```

This is also a very concrete example of usage for Kubernetes RBAC, because we
need to give Prometheus access to a list of resources in order for service
discovery to work. See [prometheus-rbac.yaml](prometheus-rbac.yaml) for details.

## Grafana

The `grafana` deployment is already configured with Prometheus as datasource and
to automatically load dashboards definitions from
`/grafana-dashboard-definitions/0`. You will find a "Kubernetes Nodes" dashboard
already provisioned to play with.

The `grafana` service is of type `NodePort`, you can access it on port `30300`.

## Alertmanager

The `alertmanager` service is of type `NodePort`, you can access it on port
`30993`.

## Maildev 

Maildev is used as a test appliction for email sent by alertmanager and it's web interface is exposed with a service of type `NodePort` on port `30080`