# kubernetes-sandbox

## Prerequisites

```
brew install kind
```

## Set up

```
kind create cluster --name sandbox --image=kindest/node:v1.26.3
```

## Example

```
kubectl appl -f manifests/namespaces.yaml
```
