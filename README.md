Hello,

I have designed a Kubernetes Cluster which manages deployment of a nginx app. I have shown how can we pull whole cluster logs through elastic search and see it through Kibana outside.
The whole architecture is monitored by Grafana and we can add our own alerts as per the requirement.

Assumptions:

There are two dockerfile 

App
firdous24/nginx:v2

Side car
firdous24/fluentbit:v2
