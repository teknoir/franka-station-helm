# Franka Station Helm

`franka-station` is the umbrella Helm chart for the Franka Arm surrogate lab station. It
aggregates the component charts: `franka-cameras`, `franka-pcf`, `franka-ros`, and
`franka-zenoh-router`.

- Repo: `https://teknoir.github.io/franka-station-helm`
- Chart: `franka-station`

## Deploy on an edge device

Commit a K3s `HelmChart` resource to GitOps (or add it through a Devstudio `add-app` node).

```yaml
apiVersion: helm.cattle.io/v1
kind: HelmChart
metadata:
  name: franka-station
  namespace: default
spec:
  repo: https://teknoir.github.io/franka-station-helm
  chart: franka-station
  targetNamespace: default
  valuesContent: |-
    global:
      robot: castor
```

## Key values

- `global.robot`: robot name (default `castor`).
- `global.image`: container image for ROS-based components.
- `global.nodeSelector`: node selector for pod scheduling.
