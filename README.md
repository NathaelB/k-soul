# k-soul

GitOps repository for Kubernetes cluster management using ArgoCD.

## Structure

```
.
├── apps/          # ArgoCD Applications
├── manifests/     # Kubernetes manifests (databases, etc.)
└── projects/      # ArgoCD Projects
```

## Applications

- **ferriskey**: Main application deployed from Helm chart
- **ferriskey-database**: PostgreSQL database using CloudNativePG operator
- **ferriskey-admin-secret**: Kubernetes Secret for admin credentials

## Usage

### Create a new project

```bash
kubectl apply -f projects/ferriskey.yaml
```

### Deploy Database

```bash
kubectl apply -f apps/ferriskey/database-application.yaml
```

### Create Admin Secret

```bash
kubectl apply -f apps/ferriskey/admin-secret-application.yaml
```

### Deploy Ferriskey Instance

```bash
kubectl apply -f apps/ferriskey/application.yaml
```

## Requirements

- Kubernetes cluster
- ArgoCD installed
- CloudNativePG operator installed

## How it works

ArgoCD watches this repository and automatically syncs applications to the cluster. Applications are configured with auto-sync and self-healing enabled.
