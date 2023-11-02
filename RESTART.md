minikube start --memory=12384 --cpus=4

kubectl config set-context --current --namespace=tutorial

export NAMESPACE=tutorial
export MYHOST=$(kubectl config view -o jsonpath={.contexts..namespace}).bookinfo.com

minikube tunnel

export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')

export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')

export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')

export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT

kubectl get pods -n istio-system

# look for the istio-ingressgateway
kubectl port-forward pod/istio-ingressgateway-9c8b9b586-25n52 8080 -n istio-system

alias k9s=/snap/k9s/current/bin/k9s