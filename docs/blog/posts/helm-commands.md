---
date: 2021-03-09
description: Userful helm commands
categories:
  - Commands
---

# Helm chart commands

Helm helps you manage Kubernetes applications — Helm Charts help you define, install, and upgrade even the most complex Kubernetes application. [Helm link](https://helm.sh/)

Below list most useful Helm Commands for reference.  
<!-- more -->


## Essential Toolkit for helm

### 1. version

```
helm version
```

### 2. List installed releases

```
helm list
helm get values <release>
```

### 3. install package

```
helm install -f ./override.yaml <name> <chart> [--namespace <ns>]

helm install mychart-0.1.0.tgz --dry-run --debug       # Test installing
```

### 4. upgrading releases

```
helm upgrade <name> [--namespace <ns>]
helm upgrade --wait <name>   # Wait for pods to come up
```

### 5. delete release

```
helm delete --purge <name>
```

### 6. get release

```
helm get <deployment-name>
```

### 7. helm lint

```
helm lint <chart-name>
```