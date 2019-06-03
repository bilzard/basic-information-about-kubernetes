# 1. Kubernetes Architecture

## The Control Plane

* cluster's brain
    * it runs all the tasks required for Kubernetes to do its job
        * scheduling containers
        * manageng Services
        * serving API requests
        * etc.
* control plain is made up with components:
    * kube-apiserver
        * the frontend server for control plane that serves API requests
    * etcd
        * the database where Kubernetes stores all its information
            * what nodes exists?
            * what resources exists in the cluster?
            * etc.
    * kube-scheduler
        * decides where to run the newly created Pods
    * kube-controller-manager
        * responsible for running resource controller ex) Deployments
    * cloud-controller-manager
        * interacts with the cloud provider
            * managing resources such as
                * load balancers
                * disk volumes
                * etc.
* master nodes
    * the members of the cluster which run the control plane components

## Node Components

* worker nodes
    * the cluster members that run user workloads
* each worker node in Kubernetes cluster runs these components:
    * kubelet
        * responsible for driving the container runtime to start workloads that are scheduled on the nodes, and monitoring its status
    * kube-proxy
        * does networking that routs requests between Pods on different nodes, and between Pods and the internet
    * Container runtime
        * actually starts and stops containers and handles their communications
        * usually Docker, but Kubernetes supports other container runtimes such as rkt and CRI-O

![kubernetes-components](https://i.imgur.com/LC7Uexl.jpg)
Source: *[Cloud Native DevOps With Kubernetes](https://www.nginx.com/resources/library/cloud-native-devops-with-kubernetes/)*
