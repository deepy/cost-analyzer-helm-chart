# cost-analyzer helm chart
Helm chart for the Kubecost project, which is created to monitor and manage Kubernetes resource spend. Please contact team@kubecost.com or visit [kubecost.com](http://kubecost.com) for more info.

While Helm is the recommended install path, these resources (with the default configuration options below) can also be created with the following command: 
  
`kubectl apply -f https://raw.githubusercontent.com/kubecost/cost-analyzer-helm-chart/master/kubecost.yaml --namespace kubecost`


Parameter | Description | Default
--------- | ----------- | -------
`global.prometheus.enabled` | If true, use an existing Prometheus install. More info [here](http://docs.kubecost.com/custom-prom). | `false`
`prometheus.server.persistentVolume.enabled` | If true, Prometheus server will create a Persistent Volume Claim. | `true`
`prometheus.server.persistentVolume.size` | Prometheus server data Persistent Volume size. Default set to retain ~6000 samples per second for 15 days. | `32Gi`
`prometheus.server.retention` | Determines when to remove old data. | `15d`
`prometheus.server.resources.limits.memory` | Set a memory limit on Prometheus server container. | `not set`
`prometheus.server.resources.limits.cpu` | Set a CPU limit on Prometheus server container. | `not set`
`prometheus.nodeExporter.enabled` `prometheus.serviceAccounts.nodeExporter.create` | If false, do not crate NodeExporter daemonset.  | `true`
`persistentVolume.enabled` | If true, Kubecost will create a Persistent Volume Claim for product config data.  | `true`
`persistentVolume.size` | Define PVC size for cost-analyzer  | `0.2Gi`
`ingress.enabled` | If true, Ingress will be created | `false`
`ingress.annotations` | Ingress annotations | `{}`
`ingress.paths` | Ingress paths | `["/"]`
`ingress.hosts` | Ingress hostnames | `[cost-analyzer.local]`
`ingress.tls` | Ingress TLS configuration (YAML) | `[]`
`networkPolicy.enabled` | If true, create a NetworkPolicy to deny egress  | `false`
`serviceMonitor.enabled` | Set this to `true` to create ServiceMonitor for Prometheus operator | `false`
`serviceMonitor.additionalLabels` | Additional labels that can be used so ServiceMonitor will be discovered by Prometheus | `{}`
`prometheusRule.enabled` | Set this to `true` to create PrometheusRule for Prometheus operator | `false`
`prometheusRule.additionalLabels` | Additional labels that can be used so PrometheusRule will be discovered by Prometheus | `{}`
`grafana.sidecar.datasources.defaultDatasourceEnabled` | Set this to `false` to disable creation of Prometheus datasource in Grafana | `true`
