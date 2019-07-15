kubectl apply -f namespace.yaml

kubectl label namespace default istio-injection=enabled

kubectl delete meshpolicies.authentication.istio.io default

helm template istio-init --name istio-init --namespace istio-system | kubectl apply -f -

helm template ./istio --name istio --namespace istio-system --values values.yaml | kubectl apply -f -
