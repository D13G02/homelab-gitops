# Homelab GitOps

This repository implements the GitOps methodology for managing the homelab Kubernetes clusters. It serves as the single source of truth, defining the entire desired state of all applications and resources deployed across the infrastructure.

## Key Features

- **Declarative Cluster State**: Contains the complete YAML manifests that define what should be running in each cluster, including applications, namespaces, and configurations.
- **Multi-Cluster Ready**: Organized to support multiple clusters and environments (development, staging, production) from a single repository.
- **GitOps Native**: Designed to be consumed by ArgoCD or Flux, enabling automated synchronization between the repository and the live clusters.

## Structure

- **`/clusters/`**: Contains environment and cluster-specific configurations. Each subdirectory represents a distinct cluster (e.g., `dev/lab01`).
- **`/environments/`**: Base directory for organizing configurations by environment (development, staging, production).
- **`/globals/`**: Houses resources that are common across all clusters, promoting DRY (Don't Repeat Yourself) principles.

## Technologies

- **ArgoCD**: The primary GitOps engine that continuously reconciles the cluster state with this repository.
- **Kubernetes**: All resources are defined in native Kubernetes YAML manifests.

## Relationship with Other Repositories

This repository is part of a larger homelab ecosystem:

- **`homelab-automation`**: Provisions and configures the underlying infrastructure (VMs, OS, k0s installation).
- **`homelab-catalog`**: Stores reusable component definitions (Helm charts, Kustomize bases) that this repository can reference and deploy.

This repository acts as the **orchestration layer**, defining the final state that the infrastructure and catalog components work together to achieve.
