# Setup istio and Ambassador with bookinfo example and kubernetes-dashboard

## Setup istio
`kubectl apply -f install/kubernetes/helm/istio/templates/crds.yaml`
`kubectl apply -f install/kubernetes/istio-demo.yaml`
`kubectl get svc -n istio-system`
`kubectl get pods -n istio-system`

## Setup bookinfo example
`kubectl label namespace default istio-injection=enabled`
`kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml`
`kubectl apply -f samples/httpbin/httpbin.yaml`
```
kubectl get services
kubectl get pods
```
`kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml`
`kubectl get gateway`
`kubectl apply -f samples/bookinfo/networking/destination-rule-all.yaml`

## install Ambassador
`kubectl apply -f https://getambassador.io/yaml/ambassador/ambassador-rbac.yaml`
`kubectl apply -f ambassador-service.yaml`
`kubectl get services`

### modify bookinfo
`kubectl apply -f bookinfo.yaml`

`kubectl delete ingress gateway`

http://localhost:32732/ambassador/v0/diag/