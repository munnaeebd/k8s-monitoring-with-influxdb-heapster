# k8s-monitoring-with-influxdb-heapster
~~~
namespace	SHOW TAG VALUES FROM "uptime" WITH KEY = "namespace_name"

pod	SHOW TAG VALUES FROM "uptime" WITH KEY = "pod_name" where "namespace_name" =~ /^$namespace$/
~~~
query:
~~~
SELECT mean("value") FROM "cpu/usage_rate" WHERE ("pod_name" =~ /^$pod$/ AND "namespace_name" =~ /^$namespace$/) AND $timeFilter GROUP BY time($__interval) fill(none)
~~~
