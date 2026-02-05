# Instalación de JFrog Artifactory usando Helm Charts

Este documento describe cómo instalar JFrog Artifactory en Kubernetes/OpenShift utilizando Helm Charts.

## Prerequisitos

- Kubernetes/OpenShift cluster configurado y accesible
- `kubectl` o `oc` CLI instalado y configurado
- Helm 3.x instalado
- Permisos suficientes para crear namespaces y recursos en el cluster

## 1. Configuración del Repositorio Helm

Primero, añade el repositorio oficial de JFrog a Helm:

# Añadir el repositorio (si no está ya añadido)
helm repo add jfrog https://charts.jfrog.io/
helm repo update

# Crear el namespace
oc new-project appdev-artifactory

# Instalar el chart de OpenShift

 helm install -name artifactory-oss jfrog/artifactory-oss --namespace appdev-artifactory --create-namespace --set crds.enabled=true -f jfrog-artifactory-oss-values.yaml

oc adm policy add-scc-to-user anyuid -z openshiftartifactoryha-artifactory-ha -n appdev-artifactory  

oc create route edge artifactory --service artifactory-oss --port 8082


# Desinstalar
Para desinstalar Artifactory:
helm uninstall artifactory-oss -n artifactory