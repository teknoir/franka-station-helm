# Franka Station Helm Charts

This repository contains a collection of Helm charts for deploying the ROS 2 stack and associated components for Franka robot stations.

## Project Structure

The project is organized into a modular set of Helm charts located in the `charts/` directory:

- **`franka-station`**: An umbrella chart that aggregates the core components of a Franka station.
- **`franka-cameras`**: Deployment for station cameras.
- **`franka-pcf`**: Deployment for the Persona Control Framework (PCF).
- **`franka-ros`**: Deployment for the Franka ROS 2 stack.
- **`franka-zenoh-router`**: Deployment for the Zenoh router to facilitate communication.
- **`teleop-station`**: Chart for the teleoperation station components.

Additional directories:
- **`test/`**: Contains sample configurations and resources for testing (e.g., hardware config maps).

## Getting Started

### Prerequisites

- [Helm](https://helm.sh/docs/intro/install/) (v3+)

### Update Dependencies

The `franka-station` umbrella chart uses local file dependencies. Before rendering or installing, update the dependencies:

```bash
helm dependency update charts/franka-station
```

### Rendering Templates

To see the rendered Kubernetes manifests:

```bash
# Default (robot: castor)
helm template charts/franka-station

# Overriding the robot name
helm template charts/franka-station --set global.robot=pollux
```

## Configuration

The charts use a `global` section in `values.yaml` to share configuration across subcharts. Key parameters include:

- `global.robot`: The name of the robot (default: `castor`).
- `global.image`: The container image to use for ROS-based components.
- `global.nodeSelector`: Kubernetes node selector for scheduling pods.
