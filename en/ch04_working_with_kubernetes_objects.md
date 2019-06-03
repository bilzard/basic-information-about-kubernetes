# Chap04. Working with Kubernetes Objects

## Pods, Deployments, and Services

* Pod = "group of whales"
    * fundamental unit of work in kubernetes
    * specifying a single container or group of communicating containers that are scheduled together
* Deployment
    * high-level Kubernetes resources that declaratively manages Pods, deploying, scheduling, updating, and restarting them when necessary
* ReplicaSet
    * responsible for a group of identical Pods, or *replicas*
    * control the number of replicas that are specified in the specification
    * if there are too few (or too many) Pods, compared to the specification, the ReplicasSet controller will start (or stop) some Pods to rectify the situation
* Service
    * the Kubernetes equivalent of a load balancer or proxy
    * routing traffic to its matching Pods via a single, well-known, durable IP address or DNS name
* *reconciliation loop*
    * the process that Kubernetes controllers continuously check the desired state specified by each resource against the actual state of the cluster, and make any necessary adjustments to keep them sync
* Kubernetes scheduler
    * watches for a Pod that isn't yet running on any node, finds a suitalbe node for it, and instructs the kubelet on that node to run the Pod
    * Reference:
        * https://jvns.ca/blog/2017/07/27/how-does-the-kubernetes-scheduler-work/
* kubectl
    * a CLI tool that enables you to access Kubernetes control plain's APIs
* helm
    * a Kubernetes package manager
* helm chart
    * helm package

![deployments-replicasets-and-pods](https://i.imgur.com/UHgZbAA.jpg)
