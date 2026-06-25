# Teleop Station App

The Teleop Station App is the deployed teleoperation workstation. It runs on a
Teknoir-managed edge device (the teleop workstation, e.g. `castor`) and is composed from the
`teleop-station` Helm chart, which runs the scene runner with the robot configuration
mounted from a ConfigMap.

## Deploy on an edge device

Commit a K3s `HelmChart` resource to GitOps (or add it through a Devstudio `add-app` node)
that points at the `teleop-station` chart.

```yaml
apiVersion: helm.cattle.io/v1
kind: HelmChart
metadata:
  name: teleop-station
  namespace: default
spec:
  repo: https://teknoir.github.io/franka-station-helm
  chart: teleop-station
  targetNamespace: default
  valuesContent: |-
    global:
      robot: castor
```

See the teleop-station-helm chart docs for the full value reference.
