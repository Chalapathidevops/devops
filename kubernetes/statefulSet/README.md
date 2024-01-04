# StatefulSet

A StatefulSet in Kubernetes is like a system that manages a group of closely related, stateful applications, such as databases, ensuring that each application instance gets its unique identity and persistent storage. It maintains the order of deployment, allowing reliable scaling and management of stateful applications within the Kubernetes cluster.

* **Purpose:** StatefulSets are a way to manage stateful applications within Kubernetes, providing stable, unique identities and persistent storage for each instance (Pod) in the set.
* **Statefulness:** They're designed for applications that have a sense of identity or state, like databases, queues, or applications requiring stable network identifiers.
* **Unique Identifiers:** Each Pod created by a StatefulSet gets its own stable identifier (hostname) and persists even if the Pod is restarted or rescheduled.
* **Ordered Deployment:** Pods are deployed and scaled in a specific order, ensuring reliable startup and termination sequences.

**Benefits:**

* **Stable Identity:** Ensures that each instance maintains the same identity, even across restarts or rescheduling.
* **Persistent Storage:** Enables the use of persistent storage volumes (like PersistentVolumes or PersistentVolumeClaims) associated with each instance.
* **Ordered Operations:** Provides control over the order of Pod creation, enabling ordered startup and shutdown of instances.

```
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: cassandra
spec:
  replicas: 3
  serviceName: cassandra
  selector:
    matchLabels:
      app: cassandra
  template:
    metadata:
      labels:
        app: cassandra
    spec:
      containers:
      - name: cassandra
        image: cassandra:latest
        ports:
        - containerPort: 9042
        # Volume mounts for persistence
        volumeMounts:
        - name: cassandra-data
          mountPath: /var/lib/cassandra
  volumeClaimTemplates:
  - metadata:
      name: cassandra-data
    spec:
      accessModes: [ "ReadWriteOnce" ]
      resources:
        requests:
          storage: 1Gi
```
