# Franka PCF Helm

`franka-pcf` deploys the Persona Control Framework (PCF). It runs the hardware / controller
configuration process with its hardware ConfigMap mounted into the container.

- Repo: `https://teknoir.github.io/franka-station-helm`
- Chart: `franka-pcf`

## Deploy on an edge device

Commit a K3s `HelmChart` resource to GitOps (or add it through a Devstudio `add-app` node).

```yaml
apiVersion: helm.cattle.io/v1
kind: HelmChart
metadata:
  name: pcf
  namespace: default
spec:
  repo: https://teknoir.github.io/franka-station-helm
  chart: franka-pcf
  targetNamespace: default
  valuesContent: |-
    image: "persona-nas1.chipmunk-tuna.ts.net/persona/manipulation:jazzy-py3.12-dev-ubuntu24.04"
    nodeSelector:
      kubernetes.io/hostname: teknoir-master
```
