```
apiVersion: v1
kind: ReplicationController
metadata:
  name: new-rc
spec:
  template:
    metadata:
      name: new-pod
      labels:
        env: test
    spec:
      containers:
        - image: nginx
          name: nginximage
  replicas: 4      
```
