# kubernetes-sandbox

## Prerequisites

* [Docker](https://www.docker.com/)
* [kind](https://kind.sigs.k8s.io/)
* [helm](https://helm.sh/)
* [helmfile](https://github.com/helmfile/helmfile)
* [istioctl](https://istio.io/latest/docs/ops/diagnostic-tools/istioctl/)

## Set up

```
k8s_version=v1.29.1
kind create cluster --name "sandbox-$k8s_version" --config=cluster.yaml --image="kindest/node:$k8s_version"

# After context swiched:
helmfile init # Install diff, secrets, s3, helm-git plugin
helmfile apply
```

One-time operations:

```
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

## References

* https://istio.io/latest/docs/setup/install/helm/
