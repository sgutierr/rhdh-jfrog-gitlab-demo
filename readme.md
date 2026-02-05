# Preparation and Installation - demo RHDH

This repository contains a complete Helm chart to deploy an integrated development platform on OpenShift, including Red Hat Developer Hub (RHDH), Keycloak, GitLab, JFrog Artifactory, and ArgoCD.

## 📋 Table of Contents

- [Description](#description)
- [Components](#components)
- [Prerequisites](#prerequisites)
- [Configuration](#configuration)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Deployment Order](#deployment-order)
- [Service Access](#service-access)
- [Troubleshooting](#troubleshooting)

## 🎯 Description

This Helm chart deploys a complete DevOps development platform that includes:

- **Red Hat Developer Hub (RHDH)**: Developer portal based on Backstage
- **Keycloak**: Authentication and authorization server (SSO)
- **GitLab**: Source code management and CI/CD platform
- **JFrog Artifactory**: Artifact repository and dependency management
- **ArgoCD**: GitOps tool for continuous deployments

The deployment is organized in sequential steps using ArgoCD sync-waves to ensure the correct installation order.

## 🧩 Components

### Red Hat Developer Hub (RHDH)
- Developer portal with service catalog
- Integration with GitLab, Keycloak, ArgoCD, and Kubernetes
- Dynamic plugins for extended functionality
- Local PostgreSQL database

### Keycloak
- OIDC/OAuth2 authentication
- User and role management
- Integration with RHDH and GitLab
- Dedicated PostgreSQL database

### GitLab
- Git repository management
- CI/CD pipelines
- Project and group management
- Integration with RHDH

### JFrog Artifactory
- Artifact repository for Maven, npm, Docker, etc.
- Dependency management
- Integration with CI/CD pipelines

### ArgoCD
- GitOps for automated deployments
- Continuous synchronization with Git repositories
- Application and project management

## 📦 Prerequisites

- OpenShift 4.x cluster configured and accessible
- `oc` CLI installed and configured
- Helm 3.x installed
- Administrator permissions or sufficient permissions to:
  - Create namespaces
  - Install operators
  - Create ClusterRoles and ClusterRoleBindings
  - Create routes and services
- Access to the following operators from OpenShift Marketplace:
  - Red Hat Developer Hub Operator
  - GitLab Operator
  - Keycloak Operator (Red Hat Build of Keycloak)
  - OpenShift GitOps Operator (ArgoCD)

## ⚙️ Configuration

Before installing, you must configure the values in the `installation/values.yaml` file:

### Required Values

cluster:
  domain: apps.cluster-grlrs.grlrs.gcp.redhatworkshops.io
   