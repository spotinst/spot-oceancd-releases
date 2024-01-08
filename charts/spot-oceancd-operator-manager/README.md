# spot-oceancd-operator-manager

![Version: 0.0.3](https://img.shields.io/badge/Version-0.0.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.0.3](https://img.shields.io/badge/AppVersion-0.0.3-informational?style=flat-square)

A Helm chart for spot-oceancd-operator-manager

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm repo add oceancd https://charts.oceancd.io
$ helm repo update
$ helm install my-release oceancd/spot-oceancd-operator-manager \
  --namespace <RELEASE_NAMESPACE> \
  --create-namespace \
  --set token=<SPOT_TOKEN> \
  --set clusterId=<CLUSETR_ID> 
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| argoRollouts.controller.affinity | object | `{}` | Assign custom affinity rules to the argo-rollouts deployment |
| argoRollouts.controller.containerSecurityContext | object | `{}` | Security Context to set on argo-rollouts container level |
| argoRollouts.controller.extraArgs | list | `[]` | Additional command line arguments to pass to argo-rollouts.  A list of flags. |
| argoRollouts.controller.extraEnv | list | `[]` | Additional environment variables for argo-rollouts. A list of name/value maps. |
| argoRollouts.controller.imagePullSecrets | list | `[]` | Secrets with credentials to pull images from a private registry. Registry secret names as an array |
| argoRollouts.controller.livenessProbe | object | `{"failureThreshold":3,"httpGet":{"path":"/healthz","port":"healthz"},"initialDelaySeconds":30,"periodSeconds":20,"successThreshold":1,"timeoutSeconds":10}` | Configure liveness probe for the argo-rollouts pod |
| argoRollouts.controller.nodeSelector | object | `{}` | Node selector for argo-rollouts pods |
| argoRollouts.controller.readinessProbe | object | `{"failureThreshold":3,"httpGet":{"path":"/metrics","port":"metrics"},"initialDelaySeconds":15,"periodSeconds":5,"successThreshold":1,"timeoutSeconds":4}` | Configure readiness probe for the argo-rollouts pod |
| argoRollouts.controller.replicas | int | `1` | The number of argo-rollouts pods to run |
| argoRollouts.controller.resources | object | `{}` | Resource limits and requests for the argo-rollouts pod |
| argoRollouts.controller.tolerations | list | `[]` | Tolerations for use with node taints for argo-rollouts pods |
| argoRollouts.dashboard.affinity | object | `{}` | Assign custom affinity rules to the argo-rollouts dashboard deployment |
| argoRollouts.dashboard.containerSecurityContext | object | `{}` | Security Context to set on argo-rollouts dashboard container level |
| argoRollouts.dashboard.enabled | bool | `false` | Deploy argo-rollouts dashboard server |
| argoRollouts.dashboard.extraEnv | list | `[]` | Additional environment variables for argo-rollouts dashboard. A list of name/value maps. |
| argoRollouts.dashboard.imagePullSecrets | list | `[]` | Secrets with credentials to pull images from a private registry. Registry secret names as an array |
| argoRollouts.dashboard.nodeSelector | object | `{}` | Node selector for argo-rollouts dashboard pods |
| argoRollouts.dashboard.replicas | int | `1` | The number of argo-rollouts dashboard pods to run |
| argoRollouts.dashboard.resources | object | `{}` | Resource limits and requests for the argo-rollouts dashboard container |
| argoRollouts.dashboard.tolerations | list | `[]` | Tolerations for use with node taints for argo-rollouts dashboard pods |
| argoRollouts.general.keepArgo | bool | false | If keep argo-rollouts on delete | 
| argoRollouts.general.keepCRDs | bool | true | If keep argo-rollouts crds on delete | 
| argoRollouts.general.keepNamespace | bool | false | If keep argo-rollouts namespace on delete | 
| argoRollouts.general.labels | object | `{}` | Labels to be added to argo-rollouts components |
| argoRollouts.general.namespace | string | `"argo-rollouts"` | Namespace to deploy argo-rollouts |
| argoRollouts.general.podAnnotations | object | `{}` | Annotations to be added to argo-rollouts pods |
| argoRollouts.general.podLabels | object | `{}` | Labels to be added to argo-rollouts pods |
| argoRollouts.general.serviceAccountAnnotations | object | `{}` | Annotations to be added to argo-rollouts service account |
| argoRollouts.general.serviceAnnotations | object | `{}` | Annotations to be added to argo-rollouts service |
| argoRollouts.general.serviceLabels | object | `{}` | Labels to be added to argo-rollouts service |
| operator.affinity | object | `{}` | Assign custom affinity rules to the operator deployment |
| operator.annotations | object | `{}` | Annotations to add to the operator |
| operator.extraEnv | list | `[]` | Additional environment variables for operator. A list of name/value maps. |
| operator.imagePullSecrets | list | `[]` | Secrets with credentials to pull images from a private registry. Registry secret names as an array |
| operator.keepCRDs | bool | true | If keep operator crds on delete |
| operator.labels | object | `{}` | Labels to be added to operator components |
| operator.nodeSelector | object | `{}` | Node selector for operator pods |
| operator.podLabels | object | `{}` | Labels to be added to operator pods |
| operator.resources | object | `{}` | Resource limits and requests for the operator pod |
| operator.serviceAccountAnnotations | object | `{}` | Annotations to add to the operator service account |
| operator.tolerations | list | `[]` | Tolerations for use with node taints for operator pods |
| operatorManager.affinity | object | `{}` | Assign custom affinity rules to the operator manager deployment |
| operatorManager.apiUrl | string | `"https://api.spotinst.io"` | Spot Api URL |
| operatorManager.clusterId | string | `""` | Cluster ID |
| operatorManager.deploymentAnnotations | object | `{}` | Annotations for operator manager deployment |
| operatorManager.extraVolumes | list | `[]` | Additional volumes to add to the operator manager pod |
| operatorManager.image.pullPolicy | string | `"IfNotPresent"` | Image pull policy for operator manager |
| operatorManager.image.registry | string | `"spotinst"` | Registry to use for operator manager image |
| operatorManager.image.repository | string | `"spot-oceancd-operator-manager"` | Repository to use for operator manager image |
| operatorManager.image.tag | string | `"0.0.3"` | Overrides the operator manager image tag |
| operatorManager.imagePullSecrets | list | `[]` | Secrets with credentials to pull images from a private registry. Registry secret names as an array |
| operatorManager.installation.extraVolumeMounts | list | `[]` | Additional volumeMounts to add to the operator manager installation container |
| operatorManager.installation.resources | object | `{}` | Resource limits and requests for the operator manager installation container |
| operatorManager.labels | object | `{}` | Labels to be added to operator manager components |
| operatorManager.manager.containerSecurityContext | object | `{"allowPrivilegeEscalation":false}` | Security Context to set on operator-manager manager container level |
| operatorManager.manager.extraVolumeMounts | list | `[]` | Additional volumeMounts to add to the operator-manager manager container |
| operatorManager.manager.resources | object | `{}` | Resource limits and requests for the operator-manager manager container |
| operatorManager.nodeSelector | object | `{}` | Node selector for operator manager pods |
| operatorManager.podAnnotations | object | `{}` | Annotations for operator manager pods |
| operatorManager.podLabels | object | `{}` | Labels to be added to operator manager pods |
| operatorManager.podSecurityContext | object | `{"runAsNonRoot":true}` | Security Context to set on operator manager pod level |
| operatorManager.priorityClassName | string | `""` | priorityClassName for the operator manager deployment |
| operatorManager.registration.resources | object | `{}` | Resource limits and requests for the operator manager registration container |
| operatorManager.replicas | int | `1` | The number of operator manager pods to run |
| operatorManager.saasUrl | string | `"https://cluster-gateway.oceancd.io"` | Saas URL |
| operatorManager.serviceAccount.annotations | object | `{}` | Annotations to add to the operator manager service account |
| operatorManager.serviceAccount.create | bool | `true` | Specifies whether a service account for operator manager should be created |
| operatorManager.serviceAccount.name | string | `""` | The name of the service account to use for operator manager. If not set and create is true, a name is generated using the fullname template |
| operatorManager.token | string | `""` | Spot token |
| operatorManager.tokenExistingSecret | string | `""` | Use existing Secret which stores spot token. The value should be set with the `spot-token` key inside the secret. |
| operatorManager.tolerations | list | `[]` | Tolerations for use with node taints for operator manager pods |
| operatorManager.topologySpreadConstraints | list | `[]` | Assign custom TopologySpreadConstraints rules to the operator manager |

----------------------------------------------