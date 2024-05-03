## To create GKE cluster, open cloud shell and run below commands

* **Create cluster with 2 nodes** `gcloud container clusters create dev-cluster --zone us-central1-a --num-nodes 2`

* **Connect to cluster** go to the Kubernetes clusters and click on connect to get below command
  
  `gcloud container clusters get-credentials dev-cluster --zone us-central1-a --project rosy-solstice-416905`


* **Delete cluster:** `gcloud container clusters delete dev-cluster --zone us-central1-a`
