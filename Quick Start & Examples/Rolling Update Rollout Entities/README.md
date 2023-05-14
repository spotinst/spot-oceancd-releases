# Rolling Update

A rolling update strategy is the default Kubernetes deployment that replaces the existing version of pods with a new version, updating pods slowly one by one.

In this strategy, 100% of the traffic is exposed to the change at the beginning of the rollout and is not configurable on behalf of the users.

Additional phases including multiple metrics that test the change may be added after the traffic change and may either be sequential or simultaneous.

A strategy is reusable and can be used and maintained over multiple services and clusters.

