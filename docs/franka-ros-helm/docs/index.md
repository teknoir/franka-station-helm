# Franka ROS Helm

`franka-ros` deploys the Franka ROS 2 stack. It builds and launches the Franka ROS node
(`franka_node` launch) as a component Deployment on the edge device.

- Repo: `https://teknoir.github.io/franka-station-helm`
- Chart: `franka-ros`

## Deploy on an edge device

Commit a K3s `HelmChart` resource to GitOps (or add it through a Devstudio `add-app` node).

```yaml
apiVersion: helm.cattle.io/v1
kind: HelmChart
metadata:
  name: ros
  namespace: default
spec:
  repo: https://teknoir.github.io/franka-station-helm
  chart: franka-ros
  targetNamespace: default
  valuesContent: |-
    image: "persona-nas1.chipmunk-tuna.ts.net/persona/manipulation:jazzy-py3.12-dev-ubuntu24.04"
    nodeSelector:
      kubernetes.io/hostname: teknoir-master
```
