# kubernetes-sandbox

## Prerequisites

* [Docker](https://www.docker.com/)
* [kind](https://kind.sigs.k8s.io/)
* [helm](https://helm.sh/)
* [istioctl](https://istio.io/latest/docs/ops/diagnostic-tools/istioctl/)

## Set up

```
kind_version=v1.29.1
kind create cluster --name "sandbox-$kind_version" --config=cluster.yaml --image="kindest/node:$kind_version"
```

One-time operations:

```
# Install Istio
# https://istio.io/latest/docs/setup/getting-started/

# Istio version is same as istioctl version
istioctl install --set profile=default

# https://istio.io/latest/docs/setup/install/helm/
helm repo add istio https://istio-release.storage.googleapis.com/charts
helm repo update

helm install istio-base istio/base -n istio-system --create-namespace --set defaultRevision=default

helm install

# Install kiali
# https://istio.io/latest/docs/ops/integrations/kiali/
kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.20/samples/addons/
```

## Example

```
kubectl apply -f manifests/namespaces.yaml
```

## Tips

curl pod:

```
kubectl run --rm -it --image=curlimages/curl client -- sh
```

```
istioctl dashboard kiali
```
