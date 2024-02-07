# kubernetes-sandbox

## Prerequisites

```
brew install --cask docker
brew install kind
```

## Set up

```
kind_version=v1.29.1
kind create cluster --name "sandbox-$kind_version" --image="kindest/node:$kind_version"
```

## Example

```
kubectl apply -f manifests/namespaces.yaml
```
