# Everything about Kubernetes

Get started with Kubernetes

---
## Contents

1. [Overview](#Overview)
   * [Definition](#Definition)
1. [Kubernetes diagram](#Kubernetes-diagram)
1. [Vocabulaire](#Vocabulaire)
1. [Namespace](#Namespace)
1. [Benefits of Kubernetes](#Benefits-of-Kubernetes)
1. [Deploy Kubernetes Dashboard](#Deploy-Kubernetes-Dashboard)
1. [Going further](#Going-further)
   * [Docker - Kubernetes Architecture](#Docker-Kubernetes-Architecture)


## Overview
### Definition
 Kubernetes, also referred to as K8s, is an open source platform used to manage Linux Containers across private, public and hybrid cloud environments. Businesses also can use Kubernetes to manage microservice architectures. Containers and Kubernetes are deployable on most cloud providers.


## Kubernetes diagram
 The following diagram shows in a simplistic format how Kubernetes works from an architecture point of view [kubernetes infrastructure][Kubernetes-infrastructure].

* Services
    * Pr  oxy
        * minion  
            * POD 
                * Container
                * Container
            * POD
                * Container
                * Container

## minion
 The minion is the node on which all the services run. You can have many minions running at one point in time. 
 
 Each minion will host one or more POD. Each POD is like hosting a service. Each POD then contains the Docker containers. 
 
 Each POD can host a different set of Docker containers. The proxy is then used to control the exposing of these services to the outside world.

 Kubernetes has several components in its architecture. The role of each component is explained below &mius;

 * etcd − This component is a highly available key-value store that is used for storing shared configuration and service discovery. Here the various applications will be able to connect to the services via the discovery service.

 * Flannel − This is a backend network which is required for the containers.

 * kube-apiserver − This is an API which can be used to orchestrate the Docker containers.

 * kube-controller-manager − This is used to control the Kubernetes services.

 * kube-scheduler − This is used to schedule the containers on hosts.

 * Kubelet − This is used to control the launching of containers via manifest files.

 * kube-proxy − This is used to provide network proxy services to the outside world.

## Namespace

## Benefits of Kubernetes
 Kubernetes enables users to schedule, run and monitor containers, typically in clustered configurations, and automate related operational tasks. These include:

 * Deployment. Set and modify preferred states for container deployment. Users can create new container instances, migrate existing ones to them and remove the old ones.
 * Monitoring. Continuously check container health, restart failed containers and remove unresponsive ones.
 * Load balancing. Perform load balancing to distribute traffic across multiple container instances.
 * Storage. Handle varied storage types for container data, from local storage to cloud resources.
 * Optimization. Add a level of intelligence to container deployments, such as resource optimization -- identify which nodes are available and which resources are required for containers, and automatically fit containers onto those nodes.
 * Security. Manage passwords, tokens, SSH keys and other sensitive information.

## Common Kubernetes terms
 Here are basic terms to help grasp how Kubernetes and its deployment work:

 *   Cluster. The foundation of Kubernetes engine. Containerized applications run on top of clusters. It is a set of machines on which your applications are managed and run.
 *   Node. Worker machines that make up clusters.
 *   Pod. Groups of containers that are deployed together on the same host machine.
Replication Controller. An abstract used to manage pod lifecycles.
 *   Selector. A matching system used for finding and classifying specific resources.
 *   Label. Value pairs used to filter, organize and perform mass operations on a set of resources.
 *   Annotation. A label with a much larger data capacity.
 *   Ingress. An application program interface (API) object that controls external access to services in a cluster -- usually HTTP. It offers name-based virtual hosting, load balancing and Secure Sockets Layer. Once you get a grasp on some basic Kubernetes concepts, stay sharp and test your knowledge of Kubernetes terms and meanings.

## Deploy Kubernetes Dashboard
Kubernetes Dashboard is a general purpose, web-based UI for Kubernetes clusters. It allows users to manage applications running in the cluster and troubleshoot them, as well as manage the cluster itself.

```
$ minikube dashboard
```
> **IMPORTANT**  
> Read the [Access Control][AC] guide before performing any further steps. The default Dashboard deployment contains a minimal set of RBAC privileges needed to run.

## Going further
* [Kubernetes | techtarget](https://www.techtarget.com/searchitoperations/definition/Google-Kubernetes)
* [Kubernetes | youtube](https://www.youtube.com/watch?v=X48VuDVv0do)
* [Running ELK on Kubernetes with Helm](https://coralogix.com/blog/elasticsearch-logstash-kibana-on-kubernetes/)


[AC]:https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/README.md