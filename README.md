# Jump App Kustomize

This repository tries to collect all Kustomize resources in order to deploy Jump App as the Helm Charts do.

During the following subsections, it is possible to find information about every feature and integration in *Jump App* deployment based on Kustomize.

## Microservices

*Jump App* microservices deployments are supported by a set of Openshift objects that have to be created in order to make available this application:

- Deployments
- Services
- Routes
- ConfigMaps to save specific information

Please review [Kustomization.yaml](./micros/Kustomization.yaml) for more information about this kustomization process.

### Testing Jump App Objects Generation Locally

```$bash
cd micros
kustomize build .
```

## Istio Support

In order to support *Jump App* application in a service mesh environment based on Istio, it is required to perform the following actions through the respective procedure execution:

- Create *Jump App* regular resources -> Import micros as base in istio *Kustomization.yaml* file
- Add a specific annotation in every deployment -> Patch deployment objects with a specific rule
- Add a specific route definitions in every route -> Patch routes with specific rules
- Create Istio resources (*gateways, virtual services, destination rules and service mesh member role definition*) -> Add the required resource per microservice and globally

Please review [Kustomization.yaml](./istio/Kustomization.yaml) for more information about this kustomization process.

### Testing Istio Objects Generation Locally

```$bash
cd istio
kustomize build .
```

## Deployment Examples

It is possible to find "real" deployments scenarios in the following [GitHub repository](https://github.com/acidonper/jump-app-gitops/tree/kustomize)

## Author

Asier Cidon @Red Hat