## HPA

In Kubernetes, a HorizontalPodAutoscaler automatically updates a workload resource (such as a Deployment or StatefulSet),
with the aim of automatically scaling the workload to match demand.

Horizontal scaling means that the response to increased load is to deploy more Pods. 
This is different from vertical scaling, which for Kubernetes would mean assigning 
more resources (for example: memory or CPU) to the Pods that are already running for the workload.



OceanCD has added support for HPA resources that target our SpotDeployments. 
If you wish to set HPA while making use of Ocean CD, you may easily do so, by making use of the above templates

The templates in question will allow you to set HPA using Kubernetes metric server or via Prometheus.

