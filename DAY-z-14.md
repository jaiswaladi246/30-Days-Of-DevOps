# DAY-14 | Azure Kubernetes Service (AKS)

# Azure Kubernetes Service (AKS) Documentation

#### Click Below to watch the video Tutorial
[![Watch the video](https://img.youtube.com/vi/gMbmpK1HseY/0.jpg)](https://www.youtube.com/watch?v=gMbmpK1HseY)

## Overview

Azure Kubernetes Service (AKS) is a managed container orchestration service provided by Microsoft Azure. It simplifies the deployment, management, and scaling of containerized applications using Kubernetes. AKS eliminates the need for manual setup and configuration of Kubernetes clusters, allowing you to focus on application development and deployment.

## Key Features

- **Simplified Cluster Management**: AKS automates the deployment and management of Kubernetes clusters, including the underlying infrastructure, master components, and worker nodes.

- **Scalability and Availability**: AKS provides built-in scaling capabilities, allowing you to scale your applications up or down based on demand. It also offers availability zones for improved resiliency.

- **Integrated Developer Tools**: AKS integrates seamlessly with other Azure services and developer tools like Azure DevOps, Azure Container Registry, and Visual Studio Code for streamlined development and deployment workflows.

- **Security and Compliance**: AKS incorporates Azure Active Directory integration, role-based access control (RBAC), and network security policies to ensure secure access and protect your containerized applications.

## Prerequisites

Before setting up AKS, ensure you have the following prerequisites:

- An Azure subscription: You'll need an active Azure subscription to create and manage AKS clusters.

- Azure CLI: Install the Azure CLI on your local machine to interact with AKS from the command line.

- kubectl: Install kubectl, the Kubernetes command-line tool, to manage your AKS clusters.

## Getting Started

Follow these steps to set up and manage an AKS cluster:

1. [Create an AKS Cluster](docs/create-cluster.md): Learn how to create an AKS cluster using the Azure CLI or Azure portal.

2. [Deploy Applications to AKS](docs/deploy-applications.md): Explore different methods for deploying containerized applications to your AKS cluster, such as using YAML manifests or Helm charts.

3. [Scale and Manage AKS](docs/manage-cluster.md): Discover how to scale your AKS cluster, manage node pools, monitor resources, and perform upgrades and maintenance tasks.

4. [Integrate with Azure DevOps](docs/integrate-devops.md): Integrate AKS with Azure DevOps for automated CI/CD pipelines, source code management, and continuous deployment to AKS.

5. [Implement Security and Networking](docs/security-networking.md): Learn about securing your AKS cluster, implementing network policies, and enabling features like Azure Private Link and Azure Active Directory integration.

## Troubleshooting

If you encounter any issues or errors while working with AKS, refer to the troubleshooting guide for common problems and their solutions.

## Additional Resources

- [Official AKS Documentation](https://docs.microsoft.com/azure/aks/): Refer to the official Microsoft Azure documentation for comprehensive guides, tutorials, and reference materials on AKS.

- [Azure Samples](https://github.com/Azure-Samples/): Explore the Azure Samples repository on GitHub for AKS-related code samples, templates, and examples.

- [Azure Kubernetes Service Community](https://github.com/Azure/AKS): Visit the AKS community repository on GitHub for community-contributed content, discussions, and issue tracking.

# Azure Kubernetes Service (AKS) in Azure DevOps Documentation

This documentation provides guidance on integrating Azure Kubernetes Service (AKS) with Azure DevOps for seamless deployment and management of containerized applications. Here's a comprehensive guide to using AKS in Azure DevOps, including setting up CI/CD pipelines, deploying to AKS, and managing your AKS clusters.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Creating AKS Cluster](#creating-aks-cluster)
3. [Setting Up Azure DevOps Project](#setting-up-azure-devops-project)
4. [Creating CI/CD Pipelines](#creating-ci-cd-pipelines)
5. [Deploying to AKS](#deploying-to-aks)
6. [Managing AKS Clusters](#managing-aks-clusters)
7. [Additional Resources](#additional-resources)

## Prerequisites

Before you begin, ensure you have the following prerequisites:

- An active Azure subscription.
- Azure DevOps organization and project set up.
- Azure Kubernetes Service (AKS) cluster provisioned.

## Creating AKS Cluster

If you haven't already set up an AKS cluster, follow the steps in the [Azure AKS documentation](https://docs.microsoft.com/azure/aks/) to create and configure your cluster. Take note of the cluster details, such as resource group, cluster name, and connection information, as you'll need them for the subsequent steps.

## Setting Up Azure DevOps Project

To integrate AKS with Azure DevOps, you need to set up an Azure DevOps project and configure the necessary settings. Here's how to get started:

1. Create a new Azure DevOps project by following the instructions provided in the [Azure DevOps documentation](https://docs.microsoft.com/azure/devops/organizations/projects/create-project?view=azure-devops-rest-7.1).

2. Configure the project settings, including repositories, work items, and pipelines, according to your project requirements.

## Creating CI/CD Pipelines

Azure DevOps provides a rich set of capabilities for creating CI/CD pipelines to automate the build, test, and deployment processes. Follow these steps to create CI/CD pipelines for your AKS project:

1. [Create a Pipeline](docs/create-pipeline.md): Learn how to create a pipeline in Azure DevOps to define the build and release processes for your application.

2. [Configure Pipeline Triggers](docs/pipeline-triggers.md): Explore different triggers and scheduling options to automatically trigger pipeline runs based on code changes or specific time intervals.

3. [Build Docker Images](docs/build-docker-images.md): Configure your pipeline to build Docker images for your application, which will be deployed to AKS.

4. [Publish Docker Images](docs/publish-docker-images.md): Set up the pipeline to publish the built Docker images to Azure Container Registry or another container registry of your choice.

5. [Deploy to AKS](docs/deploy-to-aks.md): Define the deployment steps in your pipeline to deploy the application to AKS, leveraging Kubernetes manifests or Helm charts.

6. [Configure Environment Variables](docs/configure-environment-variables.md): Securely manage and use environment variables in your pipeline for storing sensitive information like AKS credentials.

![alt text](https://github.com/jaiswaladi246/30-Days-Of-DevOps/blob/main/Images/10.png?raw=true)
![alt text](https://github.com/jaiswaladi246/30-Days-Of-DevOps/blob/main/Images/11.png?raw=true)

## Deploying to AKS

Once you have your CI/CD pipelines set up, you can deploy your applications to AKS with ease. Follow these steps:

1. Push your code changes to the configured repository in Azure

 DevOps.

2. Observe the pipeline triggering and executing the build and release processes automatically.

3. Verify the successful deployment of your application to AKS using the specified release stages and environments.

## Managing AKS Clusters

Azure DevOps also offers capabilities to manage your AKS clusters directly from the platform. Learn how to:

- [Scale AKS Cluster](docs/scale-aks-cluster.md): Scale up or down the number of nodes in your AKS cluster to meet the application demands.

- [Upgrade AKS Cluster](docs/upgrade-aks-cluster.md): Perform upgrades of your AKS cluster to leverage new features and bug fixes provided by Azure.

- [Monitor AKS Cluster](docs/monitor-aks-cluster.md): Monitor the health, performance, and resource utilization of your AKS cluster using Azure DevOps monitoring tools.

## Additional Resources

- [Azure AKS Documentation](https://docs.microsoft.com/azure/aks/): Refer to the official Microsoft Azure documentation for more in-depth information on Azure Kubernetes Service.

- [Azure DevOps Documentation](https://docs.microsoft.com/azure/devops/): Explore the Azure DevOps documentation for comprehensive guides, tutorials, and reference materials.

- [Azure DevOps Labs](https://www.azuredevopslabs.com/): Visit Azure DevOps Labs for hands-on labs and examples related to Azure DevOps and AKS integration.

- [Azure DevOps Community](https://dev.azure.com/community): Engage with the Azure DevOps community to ask questions, share experiences, and collaborate with fellow developers.

- [Sample AKS Projects](https://github.com/Azure-Samples?term=aks&type=&language=): Browse the Azure-Samples GitHub repository for sample projects using AKS and Azure DevOps.

