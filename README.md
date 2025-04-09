# CloudResumeAPI

This project demonstrates the creation of a simple API that outputs resume information. The API is deployed in Azure Kubernetes Service (AKS) using GitOps and ArgoCD. The infrastructure is created using Terraform, and the CI/CD process is automated with GitHub Actions.

## Technology Stack:
- **Azure**
- **Kubernetes (AKS)**
- **ArgoCD**
- **GitHub Actions**
- **Terraform**
- **Docker**
- **Python/Flask**

## Installation

1. Set up **Terraform** to create the infrastructure.
2. Deploy the **Kubernetes** cluster in Azure (AKS).
3. Create a **Docker** image and push it to **Azure Container Registry** (ACR).
4. Set up **ArgoCD** to automatically deploy from GitHub.

## Getting Started

1. Deploy the infrastructure using Terraform:
    ```bash
    terraform init
    terraform apply
    ```

2. Run **GitHub Actions** for building and deploying the application:
    - The **CI/CD pipeline** will build a Docker image, push it to your ACR, and update Kubernetes manifests (deployment, service, ingress).

3. Access your deployed API:
    - If you set up Ingress, you can access it through the domain defined in `ingress.yaml`.
    - If you did not set up Ingress, the API will be accessible through the Azure LoadBalancer.

## How it Works

1. **Terraform** creates the necessary Azure resources:
    - **Azure Resource Group**
    - **Azure Kubernetes Cluster (AKS)**
    - **Azure Container Registry (ACR)**
    - **Monitor Diagnostic Settings** (optional)

2. **GitHub Actions** automates the CI/CD pipeline:
    - **Docker Build**: Builds the Docker image.
    - **Push**: Pushes the image to Azure Container Registry.
    - **Deployment**: Updates Kubernetes deployment using ArgoCD and GitOps.

3. **ArgoCD** monitors the GitHub repository for changes to Kubernetes manifests and automatically applies updates to the AKS cluster.

## Secrets & Configuration

You will need to set up a few secrets in GitHub for the CI/CD pipeline:

- **AZURE_CONTAINER_REGISTRY_USERNAME**: Username for Azure Container Registry.
- **AZURE_CONTAINER_REGISTRY_PASSWORD**: Password for Azure Container Registry.
- **ACR_NAME**: Name of your Azure Container Registry.
- **KUBECONFIG**: Kubernetes configuration file for your AKS cluster. You can obtain this from Terraform after deploying the cluster.

## Example Kubernetes Manifests

- **deployment.yaml**: Defines the Kubernetes deployment for the API.
- **service.yaml**: Defines the service that exposes the API.
- **ingress.yaml**: Optional Ingress configuration for accessing the API via a custom domain.

## Useful Links

- [Terraform Documentation](https://www.terraform.io/docs)
- [Azure Kubernetes Service (AKS) Documentation](https://learn.microsoft.com/en-us/azure/aks/)
- [ArgoCD Documentation](https://argo-cd.readthedocs.io/en/stable/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
