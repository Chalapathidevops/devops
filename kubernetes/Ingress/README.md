# What is Ingress

* Ingress exposes HTTP and HTTPS routes from outside the cluster to services within the cluster. Traffic routing is controlled by rules defined on the Ingress resource.
![image](https://github.com/Chalapathidevops/devops/assets/145283206/4e4afd7e-3c44-4b0e-8e4c-301786297909)

* An Ingress Controller in Kubernetes is like a traffic director at the entrance of a city. It manages and routes incoming internet traffic to specific services (like websites or applications) inside the Kubernetes cluster, based on defined rules. It acts as a gateway, allowing external users to access different applications within the cluster using rules specified in the Ingress resources.
* An Ingress controller in Kubernetes is a resource that manages incoming traffic into the cluster, routing it to different services based on rules defined by the user. It acts as a layer that sits between the outside world and your services, managing how external requests are directed to different applications within your Kubernetes cluster.

* **Purpose:** Ingress controllers manage external access to services within a Kubernetes cluster, acting as a traffic router or gateway.
* **Routing Rules:** They use Ingress resources (YAML definitions) to define routing rules for incoming HTTP and HTTPS traffic based on hostnames and paths.
* **Routing Based on Rules:** Ingress controllers direct traffic to specific services within the cluster based on rules defined in the Ingress resources.
* **Multiple Services:** They allow multiple services to share a single IP address, simplifying external access management.
* **Load Balancing:** Ingress controllers can implement load balancing and SSL termination for incoming traffic.
* **Example Use Case:** Suppose you have different web applications within your cluster. The Ingress controller can route traffic based on domain names or paths to the appropriate services. For instance:

```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
    - host: app1.domain.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: service-app1
                port:
                  number: 80
    - host: app2.domain.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: service-app2
                port:
                  number: 80
```
* **Load Balancer Creation:** Creating an Ingress resource in Kubernetes does not directly create a load balancer. Instead, the underlying Ingress controller provisions or configures a load balancer based on the environment (could be cloud provider-based, software-based, or other solutions) to manage incoming traffic based on the Ingress rules.
