## Features

- [Header based traffic](#header-based-traffic)
- [HPA](#hpa)
- [Multiple SpotDeployments per RolloutSpec](#multiple-spotdeployments-per-rolloutspec)
- [Strategy override](#strategy-override)
- [Secrets As Part of Arguments](#secrets-as-part-of-arguments)

### Header based traffic

OceanCD has added support for Headers Based Traffic using Istio Traffic Manager allowing to send up to 100% of your traffic
during any phase of your rollout based on a http request header value.

If you wish to set Headers Based Traffic while making use of Ocean CD, you may easily do so, by making use of [the
templates](./headers_based_traffic).

### HPA

In Kubernetes, a HorizontalPodAutoscaler automatically updates a workload resource (such as a Deployment or StatefulSet),
with the aim of automatically scaling the workload to match demand.

Horizontal scaling means that the response to increased load is to deploy more Pods.
This is different from vertical scaling, which for Kubernetes would mean assigning
more resources (for example: memory or CPU) to the Pods that are already running for the workload.

OceanCD has added support for HPA resources that target our SpotDeployments.
If you wish to set HPA while making use of Ocean CD, you may easily do so, by making use of [the example](./hpa).

The templates in question will allow you to set HPA using Kubernetes metric server or via Prometheus.

### Multiple SpotDeployments per RolloutSpec

This feature allows you to set as many clusters, namespaces and SpotDeployments as needed as part of one RolloutSpec.

Multiple SpotDeployments enable all the configured SpotDeployments to use the same services, strategies, arguments as well as failure policies.

> **Note**:
>
> - Every SpotDeployment in RolloutSpec has to be unique.
> - If more than one SpotDeployment has been configured, no traffic managers can be set as part of the RolloutSpec. For such case ensure that each of the chosen SpotDeployments are being exposed with different Kubernetes services.
> - Changes in RolloutSpec or Strategy (that belongs to RolloutSpec with multiple SpotDeployments) will be applied on all SpotDeployments belonging to the RolloutSpec.

See the [related templates](./multiple_spotdeployments_per_rolloutspec).

### Strategy override

When you change the strategy as part of the RolloutSpec, the change is implemented for all subsequent rollouts.
However, there may be times when you wish to momentarily override your strategy, to test a new one without having to perform changes to your already created RolloutSpec.
OceanCD provides a method to do so by adding to your SpotDeployment manifest, an annotation.
As long as the annotation exists, the overridden strategy will be used as part of your rollouts.

> **Note**:
> If the strategy added as part of the annotation does not exist, the one set as part of the RolloutSpec will be used.

Example of the referenced annotation you can find [here](./strategy_override).

### Secrets As Part of Arguments

When you need to get a verification arg's value from a secret you can set it directly in the VerificationTemplate using
the `secretKeyRef` field

> **Note**:
> 
> - This can only be done from VerificationTemplate you cannot set it from RolloutSpec
> - Once you set the value of the arg inside VerificationTemplate you don't need to repeat it in the RolloutSpec

See the [related templates](./secrets_as_part_of_arguments)

### Baseline Verification

The baseline feature allows users to determine the success/failure of their metrics based on a comparison made between two versions (Stable VS New Version).

A baseline should be useful to any user that has difficulties setting VerificationTemplate’s success or failure thresholds.

> **Note**:
>
> - Baseline works with: Prometheus, DataDog and NewRelic providers
> - The threshold can be one of:
>   - '<'
>   - '<='
>   - '>'
>   - '>='
>   - '='
>   - 'range'
>     - 'minRange'
>     - 'maxRange'
>     - when you set the threshold to be 'range' you should provide a minimum and maximum range in percentage [0-100]

See the [related templates](./baseline).
