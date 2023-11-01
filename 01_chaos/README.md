# Chaos engineering

Simulate one service going down

```
kubectl exec $(kubectl get pods -l app=details -o jsonpath='{.items[0].metadata.name}') -- pkill ruby
```

![detail error](../imgs/image05.png)

Get the pods and see how they get restarted

```
kubectl get pods
```