# Franka Zenoh Router Helm

`franka-zenoh-router` deploys the Zenoh router that facilitates communication between the
Franka station components on the edge device.

- Repo: `https://teknoir.github.io/franka-station-helm`
- Chart: `franka-zenoh-router`

## Deploy on an edge device

Commit a K3s `HelmChart` resource to GitOps (or add it through a Devstudio `add-app` node).

```yaml
apiVersion: helm.cattle.io/v1
kind: HelmChart
metadata:
  name: zenoh-router
  namespace: default
spec:
  repo: https://teknoir.github.io/franka-station-helm
  chart: franka-zenoh-router
  targetNamespace: default
  valuesContent: |-
    nodeSelector:
      kubernetes.io/hostname: teknoir-master
```
