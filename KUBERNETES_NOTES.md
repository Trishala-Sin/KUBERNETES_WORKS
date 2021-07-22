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
evolution of Kubernetes from Borg, Google's very own distributed workload manager.
Cloud Native Computing Foundation (CNCF) : hosts the Kubernetes project, along with other popular cloud-native projects, such as Prometheus, Fluentd, cri-o,
containerd, Helm, Envoy, and Contour, just to name a few.

Define Kubernetes : 

"Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications."
Kubernetes comes from greek word which means helmsman or ship pilot.
Kubernetes is also referred to as k8s (pronounced Kate's), as there are 8 characters between k and s.

Kubernetes was started by Google and, with its v1.0 release in July 2015, Google donated it to the Cloud Native Computing Foundation (CNCF). 

Explain the reasons for using Kubernetes.
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
*	Labels.

Explain the role of the Cloud Native Computing Foundation.




