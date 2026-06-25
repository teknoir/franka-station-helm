# Franka Cameras Helm

`franka-cameras` deploys the Franka station cameras. It runs the station camera launch flow
as a component Deployment on the edge device.

- Repo: `https://teknoir.github.io/franka-station-helm`
- Chart: `franka-cameras`

## Deploy on an edge device

Commit a K3s `HelmChart` resource to GitOps (or add it through a Devstudio `add-app` node).

```yaml
apiVersion: helm.cattle.io/v1
kind: HelmChart
metadata:
  name: cameras
  namespace: default
spec:
  repo: https://teknoir.github.io/franka-station-helm
  chart: franka-cameras
  targetNamespace: default
  valuesContent: |-
    nodeSelector:
      kubernetes.io/hostname: teknoir-master
```
