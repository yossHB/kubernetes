# Everything about Kubernetes

Get started with Kubernetes

---
## Contents

1. [Overview](#Overview)
    * [Definition](#Definition)
    * [Container](#Container)
    * [Microservice](#Microservice)
    * [Why do You Need Kubernetes](#Why-do-You-Need-Kubernetes)
1. [Kubernetes diagram](#Kubernetes-diagram)
1. [Pod](#Pod)
    * [Single container pod](#Single-container-pod)
    * [Multi container pod](#Multi-container-pod)
1. [minion](#minion)
1. [Vocabulaire](#Vocabulaire)
1. [Namespace](#Namespace)
1. [Benefits of Kubernetes](#Benefits-of-Kubernetes)
1. [Common Kubernetes terms](#Common-Kubernetes-terms)
1. [Imperative Management of Kubernetes Objects](#Imperative-Management-of-Kubernetes-Objects)
1. [Kubernetes API Reference](#Kubernetes-API-Reference)
1. [Translate a Docker Compose File to Kubernetes Resources](#Translate-a-Docker-Compose-File-to-Kubernetes-Resources)
1. [Deploy Kubernetes Dashboard](#Deploy-Kubernetes-Dashboard)
1. [Courses](#Courses)
1. [Going further](#Going-further)
    * [Docker Kubernetes Architecture](#Docker-Kubernetes-Architecture)
    * [Helm](#Helm)


## Overview
### Definition
 Kubernetes, also referred to as K8s, is an open source platform used to manage Linux Containers across private, public and hybrid cloud environments. Businesses also can use Kubernetes to manage microservice architectures. Containers and Kubernetes are deployable on most cloud providers.

### Microservice
 A microservice architecture a variant of the SOA structural style – arranges an application as a collection of loosely-coupled services. In a microservices architecture, services are fine-grained and the protocols are lightweight. The goal is that teams can bring their services to life independent of others.

### Container
A container is a small, lightweight virtual machine (VM) that does not have device drivers and shares its operating system among the applications. It is a good way to bundle and run applications in a production environment. However, you need to manage these containers in a proper way so that there is no downtime.

### Why do You Need Kubernetes
 Containers decompose applications into smaller parts and enable faster development by assigning smaller, more focused teams responsible for specific containers. However, it requires a proper system for integrating and orchestrating each of these smaller decomposed parts. Kubernetes makes this possible by introducing Pods, or a collection of containers.



## Kubernetes diagram
 The following diagram shows in a simplistic format how Kubernetes works from an architecture point of view [kubernetes infrastructure][Kubernetes-infrastructure].

* Services
    * Proxy
<<<<<<< HEAD
        * minion
            * POD
        * minion
            * POD
                * Container
                * Container
            * POD
                * Container
                * Container

## Pod
A pod is a collection of containers and its storage inside a node of a Kubernetes cluster. It is possible to create a pod with multiple containers inside it. For more [information][info]

There are two types of Pods:
### Single container pod
The "one-container-per-Pod" model is the most common Kubernetes use case; in this case, you can think of a Pod as a wrapper around a single container; Kubernetes manages Pods rather than managing the containers directly.
### Multi container pod
A Pod can encapsulate an application composed of multiple co-located containers that are tightly coupled and need to share resources. These co-located containers form a single cohesive unit of service—for example, one container serving data stored in a shared volume to the public, while a separate sidecar container refreshes or updates those files. The Pod wraps these containers, storage resources, and an ephemeral network identity together as a single unit.


## Minion
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
In Kubernetes, namespaces provides a mechanism for isolating groups of resources within a single cluster. Names of resources need to be unique within a namespace, but not across namespaces. Namespace-based scoping is applicable only for namespaced objects (e.g. Deployments, Services, etc) and not for cluster-wide objects (e.g. StorageClass, Nodes, PersistentVolumes, etc).


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

## Imperative Management of Kubernetes Objects
 Kubernetes objects can be created, updated, and deleted by using the kubectl command-line tool along with an object configuration file written in YAML or JSON. This [document][KOUCF] explains how to define and manage objects using configuration files.

## Kubernetes API Reference
 In this [document][API] contains the most basic commands for getting a workload running on your cluster.

## Translate a Docker Compose File to Kubernetes Resources
 To convert a Docker Compose to container orchestrators such as Kubernetes or OpenShift we use tool called [Komposse][kompose]

### Install Kompose
 We have multiple ways to [install Kompose][ik].

### Use Kompose
1. To convert the docker-compose.yml file to files that you can use with kubectl, run kompose convert and then kubectl apply -f <output file>.
```
$ kompose convert -f docker-compose.yaml

$ kubectl apply -f .
```
2. To see all displays a list of all pods in the current namespace, along with other information.
```
$ kubectl get po
```

## Deploy Kubernetes Dashboard
Kubernetes Dashboard is a general purpose, web-based UI for Kubernetes clusters. It allows users to manage applications running in the cluster and troubleshoot them, as well as manage the cluster itself.

```
$ minikube dashboard
```
> **IMPORTANT**
> Read the [Access Control][AC] guide before performing any further steps. The default Dashboard deployment contains a minimal set of RBAC privileges needed to run.

## Courses
* [Kubernetes | Techtarget](https://www.techtarget.com/searchitoperations/definition/Google-Kubernetes)
* [Kubernetes | Simplilearn](https://www.simplilearn.com/tutorials/kubernetes-tutorial/what-is-kubernetes)
* [Kubernetes | Youtube](https://www.youtube.com/watch?v=X48VuDVv0do&t=8770s)

## Going further
### Helm
Helm helps to manage Kubernetes applications, Helm Charts help you define, install, and upgrade even the most complex Kubernetes application. For more information see this [website][website]
* [Running ELK on Kubernetes with Helm](https://coralogix.com/blog/elasticsearch-logstash-kibana-on-kubernetes/)

[KOUCF]:https://kubernetes.io/docs/tasks/manage-kubernetes-objects/imperative-config/#:~:text=Using%20Configuration%20Files-,Imperative%20Management%20of%20Kubernetes%20Objects%20Using%20Configuration%20Files,manage%20objects%20using%20configuration%20files.
[API]:https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/#-strong-api-overview-strong-
[kompose]:https://kompose.io/
[ik]:https://kompose.io/installation/
[website]:https://helm.sh/
[info]:https://kubernetes.io/docs/concepts/workloads/pods/
[AC]:https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/README.md
