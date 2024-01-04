# CronJob

* CronJob is like a scheduler that enables you to run jobs or tasks at specified times or intervals within your cluster.
* CronJob is meant for performing regular scheduled actions such as backups, report generation, and so on
* It runs a job periodically on a given schedule, written in Cron format.
* CronJobs automate the execution of tasks or jobs at scheduled times, much like a cron utility in Unix-based systems.
* They enable the scheduling of jobs within the Kubernetes environment, allowing you to run containers or Pods according to a specified schedule.

Suppose you want to run a backup job for your database every night at midnight. In Kubernetes, you can define a CronJob to schedule this backup task.
```
apiVersion: batch/v1
kind: CronJob
metadata:
  name: database-backup
spec:
  schedule: "0 0 * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: backup-container
            image: your-backup-image:tag
            # Additional container configurations
          restartPolicy: OnFailure
```
