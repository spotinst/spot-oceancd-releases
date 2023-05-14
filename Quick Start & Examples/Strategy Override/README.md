# Override Strategy
When you change the strategy as part of the RolloutSpec, the change is implemented for all subsequent rollouts.
However, there may be times where you wish to momentarily override your strategy, to test a new one without having to perform changes to your already created RolloutSpec.
OceanCD provides a method to do so by adding to your SpotDeployment manifest, an annotation. 
As long as the annotation exists, the overridden strategy will be used as part of your rollouts.


### Notes:
 - If the strategy added as part of the annotation does not exist, the one set as part of the RolloutSpec will be used.