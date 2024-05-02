
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: new-deploy
  labels:
    app: account
spec:
  selector:
    matchLabels:
      env: prod
  replicas: 2
  template:
    metadata:
      name: new-deploy-pod
      labels:
        env: prod
    spec:
      containers:
      - image: nginx
        name: prodnginx
```

## RollingUpdate

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rol-deploy
spec:
  template:
    metadata:
      name: rol-pod
      labels:
        type: rol
    spec:
      containers:
        - image: nginx
          name: nginx
  replicas: 2
  selector:
    matchLabels:
      type: rol
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 3
      maxUnavailable: 2
```

## Recreate
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: recreate-deploy
spec:
  template:
    metadata:
      name: recreate-pod
      labels:
        type: recreate
    spec:
      containers:
        - image: nginx
          name: nginx
  replicas: 5
  selector:
    matchLabels:
      type: recreate
  strategy:
    type: Recreate
```
