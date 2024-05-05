# EFK - Elasticsearch, Fluentd, and Kibana
* EFK stands for Elasticsearch, Fluentd, and Kibana. It's a popular stack used for log management and analysis in Kubernetes and other distributed systems. Here's a simple overview of each component and how they work together:

# Architecture
![image](https://github.com/Chalapathidevops/devops/assets/145283206/ece45721-a3d0-44a8-802d-b445442a9aec)


* Logging is critical in application development. We often add log statements to our code for future reference, especially when troubleshooting issues.

* In smaller applications with lower traffic, checking logs is straightforward. You can simply run the `kubectl logs` command to access the logs for a specific pod.

* But as applications grow, especially in a microservices architecture spanning multiple instances, identifying and managing logs becomes challenging. Running `kubectl logs` on numerous pods for multiple services isn't practical.

* To address this challenge, we need an efficient log management system to quickly locate the information we need when issues arise.

## Introducing the EFK Stack
When it comes to log management in Kubernetes, the EFK stack stands out as a robust solution. `EFK, short for Elasticsearch, Fluent Bit, and Kibana, streamlines the process of collecting, processing and visualizing logs.` This stack provides a powerful set of tools for managing logs across your Kubernetes clusters, ensuring you can efficiently monitor, troubleshoot, and gain valuable insights from your applications.

**Elasticsearch:** NoSQL database based on the Lucene search engine. It provides a distributed, multitenant-capable full-text search engine with an HTTP web interface and schema-free JSON documents.

**Fluentbit:** Super fast, lightweight, and highly scalable logging and metrics processor and forwarder.
  * Fluentbit will read the logs from the application container log files present on the nodes and will push these logs to Elasticsearch, and then Kibana will be used as a visualization tool (assume UI for now) for checking those logs.

**Kibana:** Data visualization dashboard software for Elasticsearch.

## Why Fluent Bit and not others?

Indeed, there are various tools available for log management, such as Logstash, Fluentd, Filebeat, and more. However, in this article, we’re giving preference to Fluent Bit for several reasons. Fluent Bit offers all the required functionality for our logging needs, boasts impressive lightweight performance, and is built on the solid foundation of Fluentd’s architecture and design principles.

Sharing the difference between Fluentd and Fluentbit as per the official docs:

![image](https://github.com/Chalapathidevops/devops/assets/145283206/cf6ba3ce-0ec0-4a93-9be8-d166f3b68a68)

## Steps to Install EFK and get logs from the application

* Log in to cluster
* Clone the repo and `cd` to the respective directory
* Run the `kubectl apply -f . ` command to deploy all the resource.
* Check the loadbalancer for Kibana server and take the IP to access the Kibana dashboard. 
