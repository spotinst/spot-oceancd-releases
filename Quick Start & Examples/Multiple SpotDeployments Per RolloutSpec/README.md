# Multiple SpotDeployments Per RolloutSpec

This feature enables you to set as many clusters, namespaces and SpotDeployments as needed as part of one RolloutSpec.

Multiple SpotDeployments enable all of the configured SpotDeployments to use the same services, strategies, arguments as well as failure policies.


### Notes:
 - Every SpotDeployment in RolloutSpec has to be unique 


 - If more than one SpotDeployment has been configured, no traffic managers can be set as part of the RolloutSpec. For such case ensure that each of the chosen SpotDeployments are being exposed with different Kubernetes services


 - Changes in RolloutSpec or Strategy (that belongs to RolloutSpec with multiple SpotDeployments) will be applied on all SpotDeployments in that RolloutSpec
