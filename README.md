# kubernetes-sandbox

## Prerequisites

* [Docker](https://www.docker.com/)
* [kind](https://kind.sigs.k8s.io/)
* [istioctl](https://istio.io/latest/docs/ops/diagnostic-tools/istioctl/)

## Set up

```
kind_version=v1.29.1
kind create cluster --name "sandbox-$kind_version" --config=cluster.yaml --image="kindest/node:$kind_version"
```

## Example

```
kubectl apply -f manifests/namespaces.yaml
```

## Tips

```
kubectl run --rm -it --image=curlimages/curl client -- sh
```

## One-time operations

```
# Install Istio
# https://istio.io/latest/docs/setup/getting-started/
istioctl install --set profile=default
```
