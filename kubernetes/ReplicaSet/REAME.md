```
  apiVersion: apps/v1
  kind: ReplicaSet
  metadata:
    name: test-rs
  spec:
    replicas: 4
    selector:
      matchLabels:
        env: test
    template: 
      metadata:
        name: test-rs-pod
        labels:
          env: test
      spec:
        containers:
        - name: nginx
          image: nginx
```
