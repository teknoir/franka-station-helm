# Teleop Station Helm

`teleop-station` deploys the teleoperation station stack. It runs the scene runner with the
robot configuration mounted from a ConfigMap.

- Repo: `https://teknoir.github.io/franka-station-helm`
- Chart: `teleop-station`

## Deploy on an edge device

Commit a K3s `HelmChart` resource to GitOps (or add it through a Devstudio `add-app` node).

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
