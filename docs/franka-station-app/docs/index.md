# Franka Station App

The Franka Station App is the deployed Franka Arm Robot surrogate lab station. It runs on a
Teknoir-managed edge device (the lab station cluster) and is composed from the
`franka-station` umbrella Helm chart (cameras, PCF, ROS, and Zenoh router).

## Deploy on an edge device

Deployment follows the Teknoir software-management workflow: commit a K3s `HelmChart`
resource to GitOps (or add it through a Devstudio `add-app` node) that points at the
`franka-station` chart.

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

See the franka-station-helm chart docs for the full value reference.
