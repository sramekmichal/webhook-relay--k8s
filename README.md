```
kubectl create secret generic whr-credentials \
  --from-literal=key=<your token key> \
  --from-literal=secret=<your token secret>
```