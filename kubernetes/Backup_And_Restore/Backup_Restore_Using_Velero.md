### Create AWS EKS clsuster

* Chocolatey links
  https://chocolatey.org/install

* Pre-requisite links
https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html

* Create EKS cluster
`eksctl create cluster --name eksbackuprestore --node-type t2.large --nodes 1 --nodes-min 1 --nodes-max 2 --region us-east-1 --zones=us-east-1a,us-east-1b,us-east-1c`

* Get EKS Cluster service `eksctl get cluster --name eksbackuprestore --region us-east-1`

* Update Kubeconfig  `aws eks update-kubeconfig --name eksbackuprestore`

* Get EKS Pod data `kubectl get pods --all-namespaces`

* Delete EKS cluster `eksctl delete cluster --name eksbackuprestore --region us-east-1`

### CREATE AWS EKS BACKUP AND RESTORE 

1. CREATE S3 BUCKET
`aws s3api create-bucket --bucket awseksbackup --region us-east-1`
2. INSTALL VELERO CLIENT
  choco install velero
3. Install Velero on EKS [--secret-file C:\Users\Lenovo\.aws\credentials, has to be changed]
```
velero install --provider aws --plugins velero/velero-plugin-for-aws:v1.0.1 --bucket awseksbackup --backup-location-config region=us-east-1 --snapshot-location-config region=us-east-1 --secret-file C:\Users\Lenovo\.aws\credentials
kubectl get all -n velero
```
4. DEPLOY TEST APPLICATION
```
kubectl create namespace eksbackupdemo
kubectl create deployment web --image=gcr.io/google-samples/hello-app:1.0 -n eksbackupdemo
kubectl create deployment nginx --image=nginx -n eksbackupdemo
```
5. VERIFY DEPLOYMENT
`kubectl get deployments -n eksbackupdemo`
6. BACKUP AND RESTORE
```
velero backup create <backupname> --include-namespaces <namespacename>
velero backup create test1 --include-namespaces eksbackupdemo
```
7. DESCRIBE BACKUP
```
velero backup describe <backupname>
velero backup describe test1
```
8. DELETE ABOVE DEPLOYMENT
`kubectl delete namespace eksbackupdemo`
9. RESTORE BACKUP ON SAME CLUSTER.
`velero restore create --from-backup test1`

10. RESTORE ON ONTHER EKS CLUSTER
* Install the velero on both the clusters but make sure that cluster points to the same S3 bucket 
```velero install --provider aws --plugins velero/velero-plugin-for-aws:v1.0.1 --bucket awseksbackup --backup-location-config region=us-east-1 --snapshot-location-config region=us-east-1 --secret-file C:\Users\Lenovo\.aws\credentials
velero restore create --from-backup test1
```
