# Kubernetes-Learning
This repository is a structured resource for exploring and mastering Kubernetes. It provides practical examples, hands-on manifests, and clear explanations of essential concepts such as Pods, Deployments, Services, ConfigMaps, Secrets, and resource management. Whether you’re just starting your Kubernetes journey or looking to deepen your understanding of advanced topics, this repository is designed to support both learning and experimentation in a real-world context.

"kubectl create"- it creates a new resource based on the provided configuration file.If the resource already exists, kubectl create will return an error, indicating that the resource already exists.
It's typically used for creating resources that don't already exist in the cluster.

"kubectl apply" - is used to create or update resources based on the provided configuration file. If the resource already exists, kubectl apply will update the existing resource with the new configuration. 

kubectl apply is idempotent, i.e., we can apply the same configuration multiple times, and it will ensure that the resource is in the desired state. It's commonly used for both creating new resources and updating existing ones.

# CKA - Concepts to master
## Docker Architecture
## Kubernetes Architecture
     - Master/Control plane Node V/s Worker Node ( Node is nothing but a Virtual machine)
     - ApiServer :- Client interacts with the cluster using ApiServer
     - Scheduler: decide which pod to be scheduled on which node based on different factors
     - Controller Manager
     - ETCD Server - Key value database that stores the cluster state and configuration
     - Kubelet - Node-level agent that helps container management and receives instructions from Api server
     - Kube proxy - Pod to pod communication
     - Install Kubectl
     - Install single node kind-cluster
     
## Creating a Kubernetes object
     - Imperative way ( Through command or API calls)
     - Declarative way ( By creating manifest files)

- https://kubernetes.io/docs/reference/kubectl/quick-reference/ (cheatsheet for kubernetes commands)
- What is a Replica Set : https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/
- What is a Deployment : https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
- What is a Replication Controller : https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/
  
## Kubernetes Services:  
   Different applications communicate with each other within Kubernetes using a service; it is also used to access applications outside the cluster.
  There are 4 types of Services:
     - ClusterIP(For Internal access) 
     - NodePort(To access the application on a particular port)
     - LoadBalancer(To access the application on a domain name or IP address without using the port number)
     - External (To use an external DNS for routing)

 ## What is a Namespace in Kubernetes
     - Provides isolation of resources
     - Avoid accidental deletion/modification
     - Separated by resource type or environment or domain and so on
     - Resources can access each other in the same namespace with their first name by the DNS name for other namespaces    

 ## Multi Container Pod Kubernetes
      - Sidecar vs Init Container

 ## Kubernetes Daemonset,Job and Cronjob
 What is a daemonset?
 A daemon set is another type of Kubernetes object that controls pods. Unlike deployment, the DS automatically deploys 1 pod to each available node. You don't need to  update the replica based on demand; the DS takes care of it by spinning X number of pods for X number of nodes.
  
 If you create a ds in a cluster of 5 nodes, then 5 pods will be created. 
 If you add another node to the cluster, a new pod will be automatically created on the new node.
 
### Examples of daemonset
    kube-proxy
    calico - Networking CNI 
    flannel - Networking CNI 
    weave-net
    monitoring agents etc

    Cron-Job : To automate a build based on time "* * * * * " - understand the concept and the algorithm.
     Jobs : Runs once a day and task is completed - usage : automation pipeline 
     
## Static pods, manual scheduling, labels, and selectors in Kubernetes
     - static pods : control plane components NOT managed by scheduler. The scheduler is not responsible for scheduling these types of pods.
     
### Static Pods :  are special types of pods managed directly by the kubelet on each node rather than through the Kubernetes API server.

Key Characteristics of Static Pods:
Not Managed by the Scheduler: Unlike deployments or replicasets, the Kubernetes scheduler does not manage static pods.
Defined on the Node: Configuration files for static pods are placed directly on the node's file system, and the kubelet watches these files.
Some examples of static pods are: ApiServer, Kube-scheduler, controller-manager, ETCD etc

### Managing Static Pods:
SSH into the Node: You will gain access to the node where the static pod is defined.(Mostly the control plane node)
Modify the YAML File: Edit or create the YAML configuration file for the static pod.
Remove the Scheduler YAML: To stop the pod, you must remove or modify the corresponding file directly on the node.
Default location": is usually /etc/kubernetes/manifests/; you can place the pod YAML in the directory, and Kubelet will pick it for scheduling.

- static pods are stored in one single directory and kubelet just mnonitor that directory.
- /etc/kubernetes/manifests# - ls -ltr This is where all the manifests of the static pods are stored.
-  Manual scheduling in Kubernetes involves assigning a pod to a specific node rather than letting the scheduler decide.

### Labels and Selectors: 
Selectors filter Kubernetes objects based on their labels. This is incredibly useful for querying and managing a subset of objects that meet specific criteria.
Labels: Organize resources within the same or across namespaces.
Namespaces: Provide a way to isolate resources from each other within a cluster.
   
## Taints and Tolerations - day 14( Tech tutorials - p.sachdeva)

  

       
