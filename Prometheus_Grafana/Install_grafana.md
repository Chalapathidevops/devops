## Install using Helm
* **Add helm repo:** `helm repo add grafana https://grafana.github.io/helm-charts`
* **Update helm repo:** `helm repo update`
* **Install helm:** `helm install grafana grafana/grafana`
* Get the Grafana password from CLI and run the secret to get grafana password
* **Expose Grafana Service:** `kubectl expose service grafana — type=NodePort — target-port=3000 — name=grafana-ext`
