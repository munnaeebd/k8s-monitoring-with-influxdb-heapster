# k8s-monitoring-with-influxdb-heapster

helm repo add bitnami https://charts.bitnami.com/bitnami
helm  install --name influxdb-helm --namespace monitoring  bitnami/influxdb --set persistence.storageClass=csi-sc-cinderplugin --set database=k8s --set authEnabled=false



grafana dashboard:
~~~
namespace	SHOW TAG VALUES FROM "uptime" WITH KEY = "namespace_name"

pod	SHOW TAG VALUES FROM "uptime" WITH KEY = "pod_name" where "namespace_name" =~ /^$namespace$/
~~~
query:
~~~
SELECT mean("value") FROM "cpu/usage_rate" WHERE ("pod_name" =~ /^$pod$/ AND "namespace_name" =~ /^$namespace$/) AND $timeFilter GROUP BY time($__interval) fill(none)
~~~
