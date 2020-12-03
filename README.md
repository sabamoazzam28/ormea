Hello,

I have designed a Kubernetes Cluster which manages deployment of a nginx app. I have shown how can we pull whole cluster logs through elastic search and see it through Kibana outside.
The whole architecture is monitored by Grafana and we can add our own alerts as per the requirement.

Assumptions:

There are two images created through Docker file and logs of application has been mounted to a shared volume between App & FluentBit so that it could be directed to Elastic Search and reflect in Kibana.

I have used LoadBalancer to deploy  application through Helm Chart.

I have also shown how to use Grafana thorough external LoadBalancer and monitor different environment.

1)Application-firdous24/nginx:v2
2)Side car- firdous24/fluentbit:v2

At last whole process has been intigrated and deployment has been done through Ansible.

Public Endpoints:

Application : a3490e90c3d68422dbc51f4a16683983-251961633.ap-south-1.elb.amazonaws.com
Kibana : https://search-demo-es-gkimrvzkvc6zyk3u3275awc6fm.ap-south-1.es.amazonaws.com/_plugin/kibana/
Grafana : https://myrancher.devops.mhealth.tech/v3/import/hdpwnvbdpeybvmqpebzmdvpsdbldrogablosirufdnbmwedklei.yaml


You can find the whole architecture designed and output in git repo.
