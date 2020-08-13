# k8s-monitoring-with-influxdb-heapster

namespace	SHOW TAG VALUES FROM "uptime" WITH KEY = "namespace_name"

pod	SHOW TAG VALUES FROM "uptime" WITH KEY = "pod_name" where "namespace_name" =~ /^$namespace$/
