# Backstage-on-Kubernetes

To run the Backstage on Kubernetes, we need to perform following steps. 

## Run Postgres

We are going to use Postgres Helm chart for deployment, it can be found [here](#https://artifacthub.io/packages/helm/bitnami/postgresql).


First of all we need to have create a `values.yaml` file with custom configurations. 

```
global:
  postgresql:
    auth:
      postgresPassword: "backstage"
      username: "backstage"
      password: "backstage"
      database: "backstage"

primary:
  name: primary
  resources:
    requests:
      memory: 256Mi
      cpu: 100m
  persistance:
    enable: true
    size: 2Gi

```

**Commands to deploy Postgres**

```
helm repo add bitnami https://charts.bitnami.com/bitnami

helm install backstage-postgresql bitnami/postgresql --version 16.6.6  --namespace backstage --create-namespace  --values postgres/values.yaml
```

To uninstall 
```
helm uninstall backstage-postgresql
```
## Run Backstage

Following manifest file can be used to deploy the backstage itself on k8s.

```
```
