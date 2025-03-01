# yorch.cloud


Welcome to the repository for the manifests of my Kubernetes cluster! This repository contains the declarative configurations that define the state of the cluster, managed using GitOps principles. Below are details about the setup, components, and instructions to contribute or deploy this setup.

---

## 🛠️ Cluster Overview

- **Kubernetes Distribution**: [K3s](https://k3s.io/)  
  A lightweight Kubernetes distribution, perfect for home labs, small clusters, and edge computing.

- **GitOps Tool**: [ArgoCD](https://argo-cd.readthedocs.io/)  
  Manages and synchronizes the manifests in this repository with the cluster state.

- **Container Registry**: [Harbor](https://goharbor.io/)  
  A secure, scalable container registry for hosting and managing Docker images.

- **TLS Certificates**: [Cert-Manager](https://cert-manager.io/)  
  Automatically provisions and manages SSL/TLS certificates for cluster workloads.

---

## 📂 Repository Structure

```plaintext
├── apps/                # Application manifests (e.g., deployments, services, etc.)
│   ├── app1/
│   ├── app2/
├── infrastructure/      # System-level components (e.g., ArgoCD, Harbor, Cert-Manager...)
└── README.md            # This file
```

---

## 🤝 Contributing

Contributions to improve the cluster or add new applications are welcome! Submit a pull request or open an issue with your suggestions.
