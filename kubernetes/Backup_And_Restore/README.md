## What is Velero?
Velero (previously known as Heptio ARK) provides a suite of tools to backup Kubernetes resources and applications for two main purposes:
* Disaster Recovery – Recover Kubernetes cluster components and applications.
* Migration – Migrate your Kubernetes applications to another Kubernetes cluster.
  
Migrating Kuernetes applications is a compelling use case. One of the significant benefits of using Kubernetes is the predictability of the platform and consequently the portability of applications that reside on it. With the main exception of nuances with persistent storage, the Kubernetes API will fell almost indistinguishable whether it resides on prem, GKE, AKS, EKS and elsewhere. If you have your Kubernetes-based application on one provider and want to migrate it to another or duplicate it to run elsewhere for dev/test, this can easily be achieved. Especially with Velero.

The overall solution is depicted below:

![image](https://github.com/Chalapathidevops/devops/assets/145283206/a73ccdc7-3ad2-458d-8c5c-45ddbc58afc9)

Ref: https://www.virtualthoughts.co.uk/2019/06/12/introducing-velero-backup-and-dr-for-kubernetes-applications/
