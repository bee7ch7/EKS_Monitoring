### Monitoring setup
Install repos for prometheus stack:
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add stable https://kubernetes-charts.storage.googleapis.com/
helm repo update
```
Installation command:
```
helm install prometheus prometheus-community/kube-prometheus-stack
```
Add mongodb and ServiceMonitor labels to be discovered by prometheus
1. Mongodb itself:
```
kubectl apply -f mongodb/
```
2. Mongodb-exporter with overrided values for ServiceMonitor and mongodb uri
```
helm install mongodb-exporter prometheus-community/prometheus-mongodb-exporter -f values.yaml
```