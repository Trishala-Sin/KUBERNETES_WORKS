#### Kubernetes Notes: 

With modern web services, users expect applications to be available 24/7, 
and developers expect to deploy new versions of those applications several times a day. 
Containerization helps package software to serve these goals, enabling applications to be released and updated without downtime. 

Kubernetes helps you make sure those containerized applications run where and when you want, 
and helps them find the resources and tools they need to work. 
Kubernetes is a production-ready, open source platform designed with Google's accumulated experience in container orchestration, 
combined with best-of-breed ideas from the community.


It might be invovled in managing a simple cluster and its containerized applications: 
*	Deploy a containerized application on a cluster.
*	Scale the deployment.
*	Update the containerized application with a new software version.
*	Debug the containerized application.

A Kubernetes Pod is a group of one or more Containers, tied together for the purposes of administration and networking. 
A Deployment provides declarative updates for Pods and ReplicaSets.

Legacy apps : tradional applications buid on old programming paradigm.
Not all legacy apps are fit for cloud. Newer applications are cloud friendly while there exists companys which built thier success 
decades ago on top of legacy technologies - MONOLITHIC APPLICATIONS.

#### Monolith services : 

monolithic applications with all components tightly coupled and almost impossible to separate, 
a nightmare to manage and deployed on super expensive hardware.
A monolith has a rather expensive taste in hardware. 
Being a large, single piece of software which continuously grows, it has to run on a single system which has to 
satisfy its compute, memory, storage, and networking requirements.The hardware of such capacity is both complex and extremely pricey.

Since the entire monolith application runs as a single process, the scaling of individual features of the monolith is almost impossible.
However, scaling the entire application can be achieved by manually deploying a new instance of the monolith on another server, 
typically behind a load balancing appliance - another pricey solution.
During upgrades, patches or migrations of the monolith application downtime is inevitable and maintenance 
windows have to be planned well in advance as disruptions in service are expected to impact clients. 
While there are third party solutions to minimize downtime to customers by setting up monolith applications 
in a highly available active/passive configuration, they introduce new challenges for system engineers 
to keep all systems at the same patch level and may introduce new possible licensing costs.

#### Microservices and advantages : 

##### Microservices are lightweight applications written in various modern programming languages,with specific dependencies, libraries and environmental requirements. 
##### To ensure that an application has everything it needs to run successfully it is packaged together with its dependencies.

Microservices can be deployed individually on separate servers provisioned with fewer resources 
- only what is required by each service and the host system itself, helping to lower compute resource expenses.

Microservices-based architecture is aligned with Event-driven Architecture and Service-Oriented Architecture (SOA) principles, 
where complex applications are composed of small independent processes which communicate with each other through APIs over a network. 
APIs allow access by other internal services of the same application or external, third-party services and applications.

Each microservice is developed and written in a modern programming language, selected to be the best suitable for the type of service and its business function.
This offers a great deal of flexibility when matching microservices with specific hardware when required, allowing deployments on inexpensive commodity hardware.

Although the distributed nature of microservices adds complexity to the architecture, one of the greatest 
benefits of microservices is scalability. 
With the overall application becoming modular, each microservice can be scaled individually, either manually 
or automated through demand-based autoscaling.

Seamless upgrades and patching processes are other benefits of microservices architecture. 
There is virtually no downtime and no service disruption to clients because upgrades are rolled out seamlessly 
- one service at a time, rather than having to re-compile, re-build and re-start an entire monolithic application. 
As a result, businesses are able to develop and roll-out new features and updates a lot faster, 
in an agile approach, having separate teams focusing on separate features, 
thus being more productive and cost-effective.

#### From Monolith to Microservices :


*	Refactoring
migrating a decades-old application to the cloud through refactoring poses serious challenges 
and the enterprise faces the refactoring approach dilemma: 
-	a "Big-bang" approach : A so-called "Big-bang" approach focuses all efforts with the refactoring 
of the monolith, postponing the development and implementation of any new features  essentially delaying progress and possibly, in the process, even breaking the core of the business, the monolith.
-	or an incremental refactoring: This incremental approach offers a gradual transition from a legacy monolith to modern microservices architecture 
and allows for phased migration of application features into the cloud.

An incremental refactoring approach guarantees that new features are developed and implemented as modern microservices which are able to communicate 
with the monolith through APIs, without appending to the monolith's code. In the meantime, features are refactored out of the 
monolith which slowly fades away while all, or most its functionality is modernized into microservices.

business components to separate from the monolith to become distributed microservices,
 how to decouple the databases from the application to separate data complexity from application logic,
 and how to test the new microservices and their dependencies, are just a few of the decisions an enterprise is faced with during refactoring.

*	Challenges : 

Not all monoliths are perfect candidates for refactoring, while some may not even "survive" such a modernization phase. When deciding 
whether a monolith is a possible candidate for refactoring, there are many possible issues to consider.

Issues : 
1) When considering a legacy Mainframe based system, written in older programming languages - Cobol or Assembler, it may be more economical to just re-build it from the ground up as a cloud-native application. A poorly designed legacy application should be re-designed and re-built from scratch following modern architectural patterns for microservices and even containers. Applications tightly coupled with data stores are also poor candidates for refactoring.
2) Once the monolith survived the refactoring phase, the next challenge is to design mechanisms or find suitable tools to keep alive all the decoupled modules to ensure application resiliency as a whole. 
3) Choosing runtimes may be another challenge. If deploying many modules on a single physical or virtual server, chances are that different libraries and runtime environment may conflict with one another causing errors and failures. 
This forces deployments of single modules per servers in order to separate their dependencies - not an economical way of resource management, and no real segregation of libraries and runtimes, as each server also has an underlying Operating System running with its libraries, thus consuming server resources - at times the OS consuming more resources than the application module itself.

application containers came along, providing encapsulated lightweight runtime environments for application modules. Containers promised consistent software environments for developers, testers, all the way from Development to Production. Wide support of containers ensured application portability from physical bare-metal to Virtual Machines, but this time with multiple applications deployed on the very same server, each running in their own execution environments isolated from one another, thus avoiding conflicts, errors, and failures. Other features of containerized application environments are higher server utilization, individual module scalability, flexibility, interoperability and easy integration with automation tools.

success stories : 
1)	AppDirect - an end-to-end commerce platform provider, started from a complex monolith application and through refactoring was able to retain limited functionality monoliths receiving very few commits, but all new features implemented as containerized microservices.
2)	box - a cloud storage solutions provider, started from a complex monolith architecture and through refactoring was able to decompose it into microservices.
3)	Crowdfire - a content management solutions provider, successfully broke down their initial monolith into microservices.
4)	GolfNow - a technology and services provider, decided to break their monoliths apart into containerized microservices.
5)	Pinterest - a social media services provider, started the refactoring process by first migrating their monolith API.

CONTAINER ORCHESTRISATION :

With container images, we confine the application code, its runtime, and all of its dependencies in a pre-defined format. 
And, with container runtimes like runC, containerd, or cri-o we can use those pre-packaged images, to create one or more containers. 
All of these runtimes are good at running containers on a single host. 
But, in practice, we would like to have a fault-tolerant and scalable solution, 
which can be achieved by creating a single controller/management unit, after connecting multiple nodes together. 
This controller/management unit is generally referred to as a container orchestrator. 

![Containerization](https://github.com/Trishala-Sin/KUBERNETES_WORKS/blob/master/img/Container.PNG?raw=true)


#### 	Define the concept of container orchestration : 

Containers :
are an application-centric method to deliver high-performing, scalable applications on any infrastructure 
of your choice. Containers are best suited to deliver microservices by providing portable, isolated virtual environments
for applications to run without interference from other running applications.

Containers encapsulate microservices and their dependencies but do not run them directly. 
Containers run container images.
A container image bundles the application along with its runtime, libraries, and dependencies, and it represents 
the source of a container deployed to offer an isolated executable environment for the application.
Containers can be deployed from a specific image on many platforms, such as workstations, Virtual Machines, public cloud, etc.

### What Is Container Orchestration?

In Development (Dev) environments, running containers on a single host for development and testing of applications may be an option.
However, when migrating to Quality Assurance (QA) and Production (Prod) environments, 
that is no longer a viable option because the applications and services need to meet specific requirements:

*	Fault-tolerance
*	On-demand scalability
*	Optimal resource usage
*	Auto-discovery to automatically discover and communicate with each other
*	Accessibility from the outside world
*	Seamless updates/rollbacks without any downtime.

Container orchestrators are tools which group systems together to form clusters where containers' deployment 
and management is automated at scale while meeting the requirements mentioned above.
orchestrators make things much easier for operators especially 
when it comes to managing hundreds and thousands of containers running on a global infrastructure.
Most container orchestrators can:

*	Group hosts together while creating a cluster
*	Schedule containers to run on hosts in the cluster based on resources availability
*	Enable containers in a cluster to communicate with each other regardless of the host they are deployed to in the cluster
*	Bind containers and storage resources
*	Group sets of similar containers and bind them to load-balancing constructs to simplify access to containerized applications by creating a level of abstraction between the containers and the user
*	Manage and optimize resource usage
*	Allow for implementation of policies to secure access to applications running inside containers.


There are many solutions available, some are mere re-distributions of well-established container orchestration tools, 
enriched with features and with certain limitations in flexibility.
Different container orchestration tools and services available today:
*	Amazon Elastic Container Service
Amazon Elastic Container Service (ECS) is a hosted service provided by Amazon Web Services (AWS) to run Docker containers at scale on its infrastructure.
*	Azure Container Instances
Azure Container Instance (ACI) is a basic container orchestration service provided by Microsoft Azure.
*	Azure Service Fabric
Azure Service Fabric is an open source container orchestrator provided by Microsoft Azure.
*	Kubernetes
Kubernetes is an open source orchestration tool, originally started by Google, today part of the Cloud Native Computing Foundation (CNCF) project.
*	Marathon
Marathon is a framework to run containers at scale on Apache Mesos.
*	Nomad
Nomad is the container and workload orchestrator provided by HashiCorp.
*	Docker Swarm
Docker Swarm is a container orchestrator provided by Docker, Inc. It is part of Docker Engine.

### Where to Deploy Container Orchestrators?
####	Discuss different container orchestration deployment options:
####	Discuss different container orchestration options:
####	Explain the benefits of using container orchestration:
Most container orchestrators can be deployed on the infrastructure of our choice 
- on bare metal, Virtual Machines, on-premise, on public and hybrid cloud. 
Kubernetes, for example, can be deployed on a workstation, with or without a local hypervisor such as Oracle VirtualBox, 
- inside a company's data center, 
- in the cloud on AWS Elastic Compute Cloud (EC2) instances, 
- Google Compute Engine (GCE) VMs, 
- DigitalOcean Droplets, 
- OpenStack, etc.
There are turnkey solutions which allow Kubernetes clusters to be installed, with only a few commands, on top of cloud Infrastructures-as-a-Service, 
such as GCE, AWS EC2, Docker Enterprise, IBM Cloud, Rancher, VMware Tanzu, and multi-cloud solutions through IBM Cloud Private or StackPointCloud.
Last but not least, there is the managed container orchestration as-a-Service, more specifically the managed Kubernetes as-a-Service solution, 
offered and hosted by the major cloud providers, such as Amazon Elastic Kubernetes Service (Amazon EKS), Azure Kubernetes Service (AKS), 
DigitalOcean Kubernetes, Google Kubernetes Engine (GKE), IBM Cloud Kubernetes Service, Oracle Container Engine for Kubernetes, or VMware Tanzu Kubernetes Grid.


## Kubernetes 

Evolution of Kubernetes from Borg, Google's very own distributed workload manager.
Cloud Native Computing Foundation (CNCF) : hosts the Kubernetes project, along with other popular cloud-native projects, such as Prometheus, Fluentd, cri-o,
containerd, Helm, Envoy, and Contour, just to name a few.

Define Kubernetes : 

"Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications."
Kubernetes comes from greek word which means helmsman or ship pilot.
Kubernetes is also referred to as k8s (pronounced Kate's), as there are 8 characters between k and s.

Kubernetes was started by Google and, with its v1.0 release in July 2015, Google donated it to the Cloud Native Computing Foundation (CNCF). 


####	Why Use Kubernetes?
Explain the reasons for using Kubernetes.

Kubernetes' architecture is modular and pluggable. 
Not only that it orchestrates modular, decoupled microservices type applications, but also its architecture follows decoupled microservices patterns. 
Kubernetes' functionality can be extended by writing custom resources, operators, custom APIs, scheduling rules or plugins.
Kubernetes is also portable and extensible. It can be deployed in many environments such as local or remote Virtual Machines, bare metal, or in public/private/hybrid/multi-cloud setups. 
It supports and it is supported by many 3rd party open source tools which enhance Kubernetes' capabilities and provide a feature-rich experience to its users.

It is a solution for workload management in banking, education, finance and investments, gaming, information technology, media and streaming, online retail, 
ridesharing, telecommunications, and many other industries. There are numerous user case studies and success stories on the Kubernetes website:

BlaBlaCar
BlackRock
Box
eBay
Haufe Group
Huawei
IBM
ING
Nokia
Pearson
Wikimedia
And many more.

#### Discuss the features of Kubernetes.

Kubernetes offers a very rich set of features for container orchestration. Some of its fully supported features are:

*	Automatic bin packing: 
Kubernetes automatically schedules containers based on resource needs and constraints, to maximize utilization without sacrificing availability.
*	Self-healing :
Kubernetes automatically replaces and reschedules containers from failed nodes. 
It kills and restarts containers unresponsive to health checks, based on existing rules/policy. 
It also prevents traffic from being routed to unresponsive containers.
*	Horizontal scaling :
With Kubernetes applications are scaled manually or automatically based on CPU or custom metrics utilization.
*	Service discovery and Load balancing
Containers receive their own IP addresses from Kubernetes, while it assigns a single Domain Name System (DNS) name 
to a set of containers to aid in load-balancing requests across the containers of the set.
*	Automated rollouts and rollbacks
Kubernetes seamlessly rolls out and rolls back application updates and configuration changes, 
constantly monitoring the application's health to prevent any downtime.
*	Secret and configuration management
Kubernetes manages sensitive data and configuration details for an application separately from the container image, 
in order to avoid a re-build of the respective image. Secrets consist of sensitive/confidential information passed 
to the application without revealing the sensitive content to the stack configuration, like on GitHub.
*	Storage orchestration
Kubernetes automatically mounts software-defined storage (SDS) solutions to containers from local storage, external cloud providers, 
distributed storage, or network storage systems.
*	Batch execution
Kubernetes supports batch execution, long-running jobs, and replaces failed containers.
support for role-based access control (RBAC) is stable only as of the Kubernetes 1.8 release.

####	Discuss the evolution of Kubernetes from Borg.
Kubernetes is highly inspired by the Google Borg system, a container and workload orchestrator for its global operations for more than a decade. 
It is an open source project written in the Go language and licensed under the Apache License, Version 2.0.

"Google's Borg system is a cluster manager that runs hundreds of thousands of jobs, 
from many thousands of different applications, across a number of clusters each with up to tens of thousands of machines".
For more than a decade, Borg has been Google's secret, running its worldwide containerized workloads in production.
Services we use from Google, such as Gmail, Drive, Maps, Docs, etc., they are all serviced using Borg. 
the features/objects of Kubernetes that can be traced back to Borg, or to lessons learned from it, are:
*	API servers
*	Pods
*	IP-per-Pod
*	Services
*	Labels

####	Explain the role of the Cloud Native Computing Foundation.

The Cloud Native Computing Foundation (CNCF) is one of the projects hosted by the Linux Foundation. 
CNCF aims to accelerate the adoption of containers, microservices, and cloud-native applications.

CNCF hosts a multitude of projects, with more to be added in the future. 
CNCF provides resources to each of the projects, but, at the same time, each project continues to operate independently under its pre-existing governance structure
 and with its existing maintainers. 
Projects within CNCF are categorized based on achieved status: Sandbox, Incubating, and Graduated. 
At the time of this writing, a dozen projects had reached Graduated status with many more Incubating and in the Sandbox.

Graduated projects:

Kubernetes for container orchestration
Prometheus for monitoring
Envoy for service mesh
CoreDNS for service discovery
containerd for container runtime
Fluentd for logging
Harbor for registry
Helm for package management
Vitess for cloud-native storage
Jaeger for distributed tracing
TUF for software updates
TiKV for key/value store

For Kubernetes, the Cloud Native Computing Foundation:

*	Provides a neutral home for the Kubernetes trademark and enforces proper usage
*	Provides license scanning of core and vendor code
*	Offers legal guidance on patent and copyright issues
*	Creates open source learning curriculum, training, and certification for both Kubernetes administrators (CKA) and application developers (CKAD)
*	Manages a software conformance working group
*	Actively markets Kubernetes
*	Supports ad hoc activities
*	Sponsors conferences and meetup events.

####	KUBERNETES ARCHITECHTURE

we will explore the Kubernetes architecture, the components of its control plane, the master and worker nodes, 
the cluster state management with etcd 
and the network setup requirements. 
We will also learn about the Container Network Interface (CNI), as Kubernetes' network specification. 

####	Discuss the Kubernetes architecture.

At a very high level, Kubernetes has the following main components:

*	One or more master nodes, part of the control plane 
*	One or more worker nodes. 
![Containerization](https://github.com/Trishala-Sin/KUBERNETES_WORKS/blob/master/img/Components_of_KUBE.PNG?raw=true)
####	Explain the different components for master and worker nodes.

The master node provides a running environment for the control plane responsible for managing the state of a Kubernetes cluster, and it is the brain behind all operations 
inside the cluster. The control plane components are agents with very distinct roles in the cluster's management. 
In order to communicate with the Kubernetes cluster, users send requests to the control plane via 
- a Command Line Interface (CLI) tool, 
- a Web User-Interface (Web UI) Dashboard, or 
- Application Programming Interface (API).

It is important to keep the control plane running at all costs. Losing the control plane may introduce downtime, causing service disruption to clients, 
with possible loss of business. To ensure the control plane's fault tolerance, master node replicas can be added to the cluster, configured in High-Availability (HA)
mode. While only one of the master nodes is dedicated to actively manage the cluster, the control plane components stay in sync across the master node replicas.
This type of configuration adds resiliency to the cluster's control plane, should the active master node fail.

To persist the Kubernetes cluster's state, all cluster configuration data is saved to etcd. 
etcd is a distributed key-value store which only holds cluster state related data, no client workload data. 
etcd may be configured on the master node (stacked topology), or on its dedicated host (external topology) to help reduce the chances of data store 
loss by decoupling it from the other control plane agents.

With stacked etcd topology, HA master node replicas ensure the etcd data store's resiliency as well. 
However, that is not the case with external etcd topology, where the etcd hosts have to be separately replicated for HA, 
a configuration that introduces the need for additional hardware.

A master node runs the following control plane components:

#### - API Server
All the administrative tasks are coordinated by the kube-apiserver, a central control plane component running on the master node. 
The API Server intercepts RESTful calls from users, operators and external agents, then validates and processes them. 
During processing the API Server reads the Kubernetes cluster's current state from the etcd data store, and after a call's execution, 
the resulting state of the Kubernetes cluster is saved in the distributed key-value data store for persistence. 
The API Server is the only master plane component to talk to the etcd data store, both to read from and to save Kubernetes cluster state information 
- acting as a middle interface for any other control plane agent inquiring about the cluster's state.

The API Server is highly configurable and customizable. It can scale horizontally, but it also supports the addition of custom secondary API Servers, 
a configuration that transforms the primary API Server into a proxy to all secondary, 
custom API Servers and routes all incoming RESTful calls to them based on custom defined rules.

#### - Scheduler

The role of the kube-scheduler is to assign new workload objects, such as pods, to nodes. During the scheduling process, 
decisions are made based on current Kubernetes cluster state and new object's requirements.
The scheduler obtains from the etcd data store, via the API Server, resource usage data for each worker node in the cluster.
The scheduler also receives from the API Server the new object's requirements which are part of its configuration data.
Requirements may include constraints that users and operators set, such as scheduling work on a node labeled with disk==ssd key/value pair. 
The scheduler also takes into account Quality of Service (QoS) requirements, data locality, affinity, anti-affinity, taints, toleration, cluster topology, etc.
Once all the cluster data is available, the scheduling algorithm filters the nodes with predicates to isolate the possible node candidates which then are scored 
with priorities in order to select the one node that satisfies all the requirements for hosting the new workload.
The outcome of the decision process is communicated back to the API Server, which then delegates the workload deployment with other control plane agents. 

The scheduler is highly configurable and customizable through scheduling policies, plugins, and profiles. 
Additional custom schedulers are also supported, then the object's configuration data should include the name of the custom scheduler expected to make the 
scheduling decision for that particular object; 
if no such data is included, the default scheduler is selected instead.
A scheduler is extremely important and complex in a multi-node Kubernetes cluster.


#### - Controller Managers
The controller managers are control plane components on the master node running controllers to regulate the state of the Kubernetes cluster. 
Controllers are watch-loops continuously running and comparing the cluster's desired state (provided by objects' configuration data) 
with its current state (obtained from etcd data store via the API server). 
In case of a mismatch corrective action is taken in the cluster until its current state matches the desired state.

The kube-controller-manager runs controllers responsible to act when nodes become unavailable, to ensure pod counts are as expected, 
to create endpoints, service accounts, and API access tokens.

The cloud-controller-manager runs controllers responsible to interact with the underlying infrastructure of a cloud provider when nodes become unavailable, 
to manage storage volumes when provided by a cloud service, and to manage load balancing and routing.

#### - Data Store.

etcd is a strongly consistent, distributed key-value data store used to persist a Kubernetes cluster's state. 
New data is written to the data store only by appending to it, data is never replaced in the data store. 
Obsolete data is compacted periodically to minimize the size of the data store.
Out of all the control plane components, only the API Server is able to communicate with the etcd data store. 

etcd is written in the Go programming language. In Kubernetes, besides storing the cluster state,
etcd is also used to store configuration details such as subnets, ConfigMaps, Secrets, etc.

etcd's CLI management tool - etcdctl, provides backup, snapshot, and restore capabilities which come in handy 
especially for a single etcd instance Kubernetes cluster - common in Development and learning environments. 
However, in Stage and Production environments, it is extremely important to replicate the data stores in HA mode, for cluster configuration data resiliency.

Some Kubernetes cluster bootstrapping tools, such as kubeadm, by default, provision stacked etcd master nodes, 
where the data store runs alongside and shares resources with the other control plane components on the same master node.

![Containerization](https://github.com/Trishala-Sin/KUBERNETES_WORKS/blob/master/img/stacked_etcd_cluster.PNG?raw=true)

For data store isolation from the control plane components, the bootstrapping process can be configured for an external etcd topology,
where the data store is provisioned on a dedicated separate host, thus reducing the chances of an etcd failure.

![Containerization](https://github.com/Trishala-Sin/KUBERNETES_WORKS/blob/master/img/external_etcd_cluster.PNG?raw=true)

Both stacked and external etcd configurations support HA configurations. etcd is based on the Raft Consensus Algorithm which allows 
a collection of machines to work as a coherent group that can survive the failures of some of its members. 
At any given time, one of the nodes in the group will be the master, and the rest of them will be the followers. 
etcd gracefully handles master elections and can tolerate node failure, including master node failures. 
Any node can be treated as a master. 

![Containerization](https://github.com/Trishala-Sin/KUBERNETES_WORKS/blob/master/img/master_follow.PNG?raw=true)

In addition, the master node runs:

- Container Runtime
- Node Agent
- Proxy.

###	Worker Node Overview

A worker node provides a running environment for client applications. 
Though containerized microservices, these applications are encapsulated in Pods, controlled by the cluster control plane agents running on the master node. 

A Pod is the smallest scheduling unit in Kubernetes. 
It is a logical collection of one or more containers scheduled together, and the collection can be started, stopped, or rescheduled as a single unit of work. 

Pods are scheduled on worker nodes, where they find required compute, memory and storage resources to run, and networking to talk to each other and the outside world. 

Also, in a multi-worker Kubernetes cluster, the network traffic between client users and the containerized applications deployed in Pods is handled directly 
by the worker nodes, and is not routed through the master node.

A worker node has the following components:

-	Container Runtime
-	Node Agent - kubelet
-	Proxy - kube-proxy
-	Addons for DNS, Dashboard user interface, cluster-level monitoring and logging.

Although Kubernetes is described as a "container orchestration engine", it does not have the capability to directly handle containers. 
In order to manage a container's lifecycle, Kubernetes requires a container runtime on the node where a Pod and its containers are to be scheduled. 
Kubernetes supports many container runtimes:

-	Docker : although a container platform which uses containerd as a container runtime, it is the most popular container runtime used with Kubernetes
-	CRI-O : a lightweight container runtime for Kubernetes, it also supports Docker image registries
-	containerd : a simple and portable container runtime providing robustness
-	frakti : a hypervisor-based container runtime for Kubernetes

##### Components of worker node : Node - Agent : 

The kubelet is an agent running on each node and communicates with the control plane components from the master node. 
It receives Pod definitions, primarily from the API Server, and interacts with the container runtime on the node to run containers associated with the Pod. 
It also monitors the health and resources of Pods running containers.

The kubelet connects to container runtimes though a plugin based interface - the Container Runtime Interface (CRI). 
The CRI consists of protocol buffers, gRPC API, libraries, and additional specifications and tools that are currently under development. 
In order to connect to interchangeable container runtimes, kubelet uses a shim application which provides a clear abstraction layer between kubelet 
and the container runtime. 

![Containerization](https://github.com/Trishala-Sin/KUBERNETES_WORKS/blob/master/img/CRI.PNG?raw=true)

As shown above, the kubelet acting as grpc client connects to the CRI shim acting as grpc server to perform container and image operations. 
The CRI implements two services: ImageService and RuntimeService. 
The ImageService is responsible for all the image-related operations, while the RuntimeService is responsible for all the Pod and container-related operations.

Container runtimes used to be hard-coded into kubelet, but since the CRI was introduced, 
Kubernetes has become more flexible to use different container runtimes without the need to recompile. 
Any container runtime that implements the CRI can be used by Kubernetes to manage Pods, containers, and container images.

#### Worker Node Components: kubelet - CRI shims :

Shims are CRI implementations, or interfaces, specific to each container runtime supported by Kubernetes. Below we present some examples of CRI shims:

*	dockershim
With dockershim, containers are created using Docker installed on the worker nodes. Internally, Docker uses containerd to create and manage containers:

![Containerization](https://github.com/Trishala-Sin/KUBERNETES_WORKS/blob/master/img/dockershim.PNG?raw=true)
*	cri-containerd
With cri-containerd, we can directly use containerd to create and manage containers:
*	CRI-O
CRI-O enables the use of any Open Container Initiative (OCI) compatible runtime with Kubernetes. At the present, 
CRI-O supported runC and Clear Containers as container runtimes. 
However, in principle, any OCI-compliant runtime can be plugged-in.
![Containerization](https://github.com/Trishala-Sin/KUBERNETES_WORKS/blob/master/img/CRI-O.PNG?raw=true)

*	frakti 
frakti enables CRI implementation through hardware virtualization, aimed to achieve a higher level of security and isolation than the 
traditional Linux OS level containers based on cgroups and namespaces. 
The frakti CRI shim is aimed at enabling kubelet to interact with Kata Containers:

![Containerization](https://github.com/Trishala-Sin/KUBERNETES_WORKS/blob/master/img/frakti.PNG?raw=true)

####	Discuss about cluster state management with etcd.

####	Review the Kubernetes network setup requirements.

