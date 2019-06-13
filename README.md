# Kubernetes_Structure

## Kubernetes
<ol>
Google built Kubernetes and has been using it for 10 years. That it has been used to run Google’s massive systems.</br></br>  

![kubernetes-final](https://user-images.githubusercontent.com/39157936/59428050-de739280-8df9-11e9-972a-eba41df3c670.jpg)

</br>
</br>

<li><strong>What is Kubernetes</strong></li>
Kubernetes is a cluster and container management tool. It lets you deploy containers to clusters, meaning a network of virtual machines. It works with different containers, not just Docker.</br>
The basic idea of Kubernetes is to further abstract machines, storage, and networks away from their physical implementation. So it is a single interface to deploy containers to all kinds of clouds, virtual machines, and physical machines.</br></br>


<li><strong>Features of Kubernetes</strong></li>
Following are some of the important features of Kubernetes.
</br>
<ol>
<li>Continues development, integration and deployment.</li>
<li>Containerized infrastructure.</li>
<li>Application-centric management.</li>
<li>Auto-scalable infrastructure.</li>
<li>Environment consistency across development testing and production.</li>
<li>Loosely coupled infrastructure, where each component can act as a separate unit.</li>
<li>Higher density of resource utilization.</li>
</ol>

</br>
--------------------------------------------------------------------------------------------------------------------------
</br>


<li><strong>Kubernetes Components</strong></li>
Here are a few of Kubernetes concepts to help understand what it does </br>
Main Components of the Kubernetes is Master Server and nodes </br></br>

<ol> 
<li><strong>Kubernetes-Master components</strong></li></br>

<ol>
<li><strong>etcd cluster</strong></li>
etcd cluster is a distributed key value storage that stores Kubernetes cluster data. </br>
It stores the configuration information which can be used by each of the nodes in the cluster. It is a high availability key value store that can be distributed among multiple nodes. It is accessible only by Kubernetes API server as it may have some sensitive information. It is a distributed key value Store which is accessible to all.</br>
Consistent and highly-available key value store used as 'Kubernetes’ backing store for all cluster data. Always have a backup plan for etcd’s data for your Kubernetes cluster. For in-depth information on etcd. </br></br>


<li><strong>API Server</strong></li>
Kubernetes is an API server which provides all the operation on cluster using the API. API server implements an interface, which means different tools and libraries can readily communicate with it. Kubeconfig is a package along with the server side tools that can be used for communication. It exposes Kubernetes API.</br></br>


<li><strong>Kube-controller-manager</strong></li>
It runs controller processes like replication controller (sets number of replicas in a pod) and endpoints controller (populates services, pods and other objects) Component on the master that runs controllers.</br>
Logically, each controller is a separate process, but to reduce complexity, they are all compiled into a single binary and run in a single process.</br>
These controllers include:
<ol>
<li><strong>Node Controller:</strong> Responsible for noticing and responding when nodes go down.</li>
<li><strong>Replication Controller:</strong> Responsible for maintaining the correct number of pods for every replication controller object in the system.</li>
<li><strong>Endpoints Controller:</strong> Populates the Endpoints object (that is, joins Services & Pods).</li>
<li><strong>Service Account & Token Controllers:</strong> Create default accounts and API access tokens for new namespaces.</li>
</ol></br>


<li><strong>cloud-controller-manager</strong></li>
It is a responsible for managing controller processes with dependencies on the underlying cloud provider
cloud-controller-manager runs controllers that interact with the underlying cloud providers.</br>
cloud-controller-manager runs cloud-provider-specific controller loops only. You must disable these controller loops in the kube-controller-manager. You can disable the controller loops by setting the --cloud-provider flag to external when starting the kube-controller-manager.</br>
cloud-controller-manager allows cloud vendors code and the Kubernetes code to evolve independent of each other. In prior releases, the core Kubernetes code was dependent upon cloud-provider-specific code for functionality. In future releases, code specific to cloud vendors should be maintained by the cloud vendor themselves, and linked to cloud-controller-manager while running Kubernetes.</br>
The following controllers have cloud provider dependencies:
<ol>
<li><strong>Node Controller:</strong> For checking the cloud provider to determine if a node has been deleted in the cloud after it stops responding</li>
<li><strong>Route Controller:</strong> For setting up routes in the underlying cloud infrastructure.</li>
<li><strong>Service Controller:</strong> For creating, updating and deleting cloud provider load balancers</li>
<li><strong>Volume Controller:</strong> For creating, attaching, and mounting volumes, and interacting with the cloud provider to orchestrate volumes</li>
</ol></br>


<li><strong>kube-scheduler</strong></li>
Kube-scheduler helps schedule the pods (a co-located group of containers inside which our application processes are running) on the cluster nodes based on resource utilization</br>
This is one of the key components of Kubernetes master. It is a service in master responsible for distributing the workload. It is responsible for tracking utilization of working load on cluster nodes and then placing the workload on which resources are available and accept the workload. In other words, this is the mechanism responsible for allocating pods to available nodes. The scheduler is responsible for workload utilization and allocating pod to new node.</br>
</ol>
</br>

--------------------------------------------------------------------------------------------------------------------------
</br>
<li><strong>Kubernetes-Node Components</li></strong></br>

<ol>
<li><strong>Docker</li></strong>
The first requirement of each node is Docker which helps in running the encapsulated application containers in a relatively isolated but lightweight operating environment.</br>


<li><strong>kubelet</li></strong>
An agent that runs on each node in the cluster. It makes sure that containers are running in a pod.</br>
The kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy. The kubelet doesn’t manage containers which were not created by Kubernetes.</br>
This is a small service in each node responsible for relaying information to and from control plane service. It interacts with etcd store to read configuration details and wright values. This communicates with the master component to receive commands and work. The kubelet process then assumes responsibility for maintaining the state of work and the node server. It manages network rules, port forwarding, etc.</br>


<li><strong>Kubernetes Proxy Service</li></strong>
This is a proxy service which runs on each node and helps in making services available to the external host. It helps in forwarding the request to correct containers and is capable of performing primitive load balancing. It makes sure that the networking environment is predictable and accessible and at the same time it is isolated as well. It manages pods on node, volumes, secrets, creating new containers’ health checkup, etc.
kube-proxy enables the Kubernetes service abstraction by maintaining network rules on the host and performing connection forwarding.
</ol>
</ol>
</br>

--------------------------------------------------------------------------------------------------------------------------

<li><strong>Container Runtime</li></strong>

The container runtime is the software that is responsible for running containers. Kubernetes supports several runtimes: Docker, containerd, cri-o, rktlet and any implementation of the Kubernetes CRI (Container Runtime Interface).</br>


<li><strong>kubectl</li></strong>
is a command line tool that interacts with kube-apiserver and send commands to the master node. Each command is converted into an API call.

</ol>            
