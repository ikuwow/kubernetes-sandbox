# kubernetes-sandbox

## Prerequisites

* [Docker](https://www.docker.com/)
* [kind](https://kind.sigs.k8s.io/)
* [helm](https://helm.sh/)
* [helmfile](https://github.com/helmfile/helmfile)
* [istioctl](https://istio.io/latest/docs/ops/diagnostic-tools/istioctl/)

## Set up


Create cluster:

```
k8s_version=v1.29.1
kind create cluster --name "sandbox-$k8s_version" --config=cluster.yaml --image="kindest/node:$k8s_version"
```

Configure cluster:

```
helmfile init # Install diff, secrets, s3, helm-git plugin
helmfile apply
```

## Example

```
kubectl apply -f manifests/
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
