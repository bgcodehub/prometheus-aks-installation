# Prometheus AKS Installation

This project contains the necessary Kubernetes manifests to set up Prometheus within an Azure Kubernetes Service (AKS) cluster, designed to monitor both Linux and Windows nodes efficiently.

## Overview

Prometheus is an open-source systems monitoring and alerting toolkit. This repository includes configurations to deploy Prometheus in an AKS environment, along with Alertmanager for handling alerts, and node exporters for scraping metrics from both Linux and Windows nodes.

## Prerequisites

- An active AKS cluster
- `kubectl` command-line tool, configured to communicate with your AKS cluster
- Helm v3 for managing packages

## Components

The setup is divided into several components:

- **Namespace**: Isolates the Prometheus resources within a dedicated namespace.
- **RBAC**: Configures necessary roles and role bindings for Prometheus to access resources in the cluster.
- **Config**: Contains the configuration files and rules for Prometheus.
- **Deployment**: Holds the deployment manifests for Prometheus and Alertmanager.
- **Service**: Provides the service definitions to access Prometheus and Alertmanager.
- **Storage**: Contains the PersistentVolumeClaim for long-term storage of Prometheus metrics.
- **Exporters**: Includes the DaemonSets for the node-exporter and windows-exporter to collect metrics.

## Getting Started

To install the Prometheus stack into your AKS cluster, follow these steps:

1. **Namespace Creation**:
   Ensure that the Prometheus namespace is created to keep your monitoring stack isolated from other cluster resources.

2. **RBAC Configuration**:
   Apply the RBAC configurations to grant Prometheus the necessary permissions to function correctly.

3. **Configuration and Rules Setup**:
   Deploy the config maps and rules for Prometheus, which define how Prometheus scrapes metrics and the alerting conditions.

4. **Deploy Prometheus and Alertmanager**:
   Use the deployment manifests to roll out Prometheus and Alertmanager to your cluster.

5. **Service Exposure**:
   Apply the service definitions to expose Prometheus and Alertmanager, making them accessible within your cluster network.

6. **Storage Configuration**:
   Set up the persistent storage to ensure that your Prometheus data is retained across pod restarts and rescheduling.

7. **Exporters Deployment**:
   Deploy the node-exporter to collect metrics from Linux nodes, and the windows-exporter for Windows nodes.

## Usage

Once deployed, you can access the Prometheus web UI and Alertmanager interface through their respective services.

## Monitoring Windows Nodes

Special attention is required for monitoring Windows nodes due to the differences in operating system. The windows-exporter DaemonSet should be deployed to these nodes to collect appropriate metrics.

## Contributing

We welcome contributions. Please follow the standard fork, branch, and pull request workflow.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for full details.

## Additional Resources

- For detailed Prometheus concepts and configuration options, please refer to [Prometheus documentation](https://prometheus.io/docs/introduction/overview/).
- To understand more about AKS, consult the [AKS documentation](https://docs.microsoft.com/en-us/azure/aks/).
- Helm's package management usage can be found in the [Helm documentation](https://helm.sh/docs/).