# kubernetes
# What is Kubernetes?
The short answer: Originally developed by Google, Kubernetes is an open-source automation and management environment for deploying containerized applications.

Kubernetes maintains high levels of availability and scalability while managing the entire lifecycle of these containerized applications and services. And since it is a platform developed for container orchestration, Kubernetes deploys containers based on OS-level virtualization instead of hardware virtualization.

System-level containers are decoupled from the underlying infrastructure and host file system, meaning they see only their own processes, have their own file systems, and their resource usage can be limited. This enables their portability across infrastructure providers, clouds, and OS distributions.

Plus, compared to VMs, containers are easy to build. This is because VMs require more resources than containers, whereas containers share a common OS kernel, making them simple to reproduce.

# Common Kubernetes Terms
Kubernetes uses nomenclature that may differ from other, similar platforms. To provide clarity for the content in this guide, here are some common terms you may come across:

Pods—groups of one or more containers deployed together on the same host, with shared resources (e.g., IP address) and a specification for how the containers should be operated.
ReplicaSet—which ensures that a specified number of pod replicas is running at any one time, with support for set-based selector requirements.
Deployments—processes that create, manage, and provide declarative updates for pods. Deployments can be used with a service tier to ensure availability or scalability.
Services—sometimes called microservices, these abstractions define a logical set of pods and a policy by which to access them. Kubernetes services provide naming, load balancing, and discovery to isolate one microservice from another.

# Key Benefits Of Kubernetes
Organizations that choose to employ Kubernetes benefit from its immutability, declarative configuration, and self-healing capabilities.

Immutability. Unlike traditional computing systems that replicate updates and log changes within an existing set of rules, Kubernetes builds an entirely new container image for each update or change it creates. This means Kubernetes adheres to the principles of immutable infrastructure—that is, user modifications do not change an artifact once it is created in the system.

There are several advantages to building a new container image for every new instance. First, it is easier to compare two different container images rather than comparing different versions of a single system image. Also, the old container image is retained and can be used as a quick rollback if an error occurs.

Declarative configuration. As an alternative to an imperative configuration which defines actions, the declarative configuration defines states. With Kubernetes, all aspects of the platform are declarative configuration objects that “declare” the desired system state.

Imperative configuration describes computation in terms of various statements that change its state. Declarative programming, on the other hand, expresses the logic of computation without describing its control flow, meaning the effects of a change can be understood before it happens. This makes declarative configuration and, subsequently, Kubernetes less prone to error.

Combined with version control, the imperative configuration makes rollbacks easier than ever. With Kubernetes’ complete dedication to maintaining the declared state, a rollback is simply a matter of “restating” the previously declared state.

Self-healing. Self-healing refers to the automated repair actions inside the system. For example, if a container fails, Kubernetes automatically restarts it. Similarly, if a node dies, the platform replaces and reschedules containers accordingly.

As previously noted, Kubernetes maintains the desired state of its configuration based on a set of predefined actions. It continually safeguards against exceptions or failures that threaten the stability and reliability of your system with minimal involvement from your team.

Traditional computing systems, on the other hand, rely heavily on human intervention every time there's an issue. Not only does this manual process require constant attention from your team, it is also prone to human error.

# Architecture
Kubernetes uses a distributed computing model that creates clusters by grouping together physical or virtual machines within a shared communication network. All Kubernetes capabilities and workloads are configured at the cluster level.

Of course, you can’t have a group work effectively without a leader. Enter the master server, which serves as the primary point of contact for the cluster. The master server is the gateway and manager for the group. It exposes an API for users and clients, schedules work, provides health checks for other servers and coordinates communication between components.

All other machines within the group or cluster are considered nodes. Their job is to take commands from the master server, run container runtimes (e.g., docker) and expose networking and storage resources to applications. These nodes also create or dismiss containers according to the master server’s direction.

Common applications and services operate inside the container clusters. They are preprogrammed to execute a specific action depending on the desired state. Cluster management is easily performed via the main API, either directly or indirectly through corresponding clients or libraries.

To start up an application or service, a declarative plan is submitted in JSON or YAML. It usually defines what should be created and how it should be communicated to the master server. Then the master server examines the requirements and the current state of the system and deploys the plan on the infrastructure.

# Deployment
Kubernetes deployments consist of the common workloads inside the platform and can be created and managed directly from the main interface. These workloads are designed to ease the lifecycle management of the replicated pods. By changing the configuration of deployments, Kubernetes automatically adjusts the replica sets and manages transitions between different applications.

With deployments, you have objects and controllers. Deployment objects describe a desired state and deployment controllers use them to change the actual state at any given moment.

Deployments can be used in the following ways:

Creating a deployment to roll out a ReplicaSet
Rolling back to an earlier deployment revision
Declaring a new state for pods
Pausing the deployment
Scaling up the deployment to facilitate an additional load
Kubernetes dashboard. To make the deployment process easy, use the Kubernetes dashboard, a web-based user interface that enables you to deploy containerized applications to a Kubernetes cluster.

Typically, you are able to get a high-level overview of the platform and manage various items —like monitor cluster applications, create or modify individual Kubernetes resources and manage attendant cluster resources—from a single dashboard.

# Kubernetes Vs. Docker Swarm
Because of Kubernetes’ recent surge in popularity, you may already be familiar with the term “Docker Swarm.” Similar to Kubernetes, Docker was originally created to package and distribute containerized applications. It acts as the default container runtime for Kubernetes. Both are open-source platforms that focus on container orchestration under the rules established by the Cloud Native Computing Foundation (CNCF).

Differences between Kubernetes and Docker Swarm. As the name suggests, Docker Swarm is a native solution created and owned by Docker, Inc., whereas Kubernetes was created by Google and donated to the CNCF.

Their main differences include the following:

Kubernetes deploys applications using a combination of pods, deployments, and services whereas Docker Swarm deploys applications as services in a Swarm cluster.
Kubernetes health checks include liveness and readiness of the apps, while Docker Swarm health checks are limited to a binary check of the container backing a service (i.e., running state or not running state).
Kubernetes features a flat networking model, enabling all pods to communicate with each other. Docker Swarm has a node joining a Swarm cluster. It creates an overlay network for services that span all the hosts in the Swarm and a host-only Docker bridge network for containers.
Kubernetes services can be discovered using environmental variables or DNS, while Docker Swarm Manager node assigns each service a unique DNS name and load balances that run containers.
Kubernetes scales to 5,000-node clusters (with multiple clusters used to scale further), while Docker Swarm scales to 30,000 containers and 1,000 nodes with one Swarm Manager.
# Kubernetes Vs. Mesos
In addition to Docker Swarm and Kubernetes, Mesos is another open-source platform used to orchestrate containers. It offers a practical and robust way for enterprises to operate containers at scale, with the following differences:

Kubernetes is solely dedicated to Docker container orchestration, while Mesos can run multiple mission-critical workloads, including Docker containers, legacy applications, and distributed data services.
Kubernetes health checks include liveness and readiness of apps, while Mesos health checks can be specified to run against the tasks inside the app.
Kubernetes features a flat networking model, enabling all pods to communicate with each other, while Mesos networking can be configured in the host mode (with containers using host ports) or the bridge mode (with container ports being bridged to host ports).
Kubernetes services can be discovered using environmental variables or DNS, while Mesos services can be discovered using DNS records associated with IPs and ports.
Kubernetes scales to 5,000-node clusters (with multiple clusters used to scale further), while Mesos scales to 10,000 nodes.

# Kubernetes & AWS Integration
According to a 2017 survey conducted by the CNCF, 63% of respondents use Kubernetes deployments on Amazon Web Services (AWS). That shouldn’t be a surprise given Amazon’s popularity across industries and markets.

However, historically, AWS has required a great deal of manual configuration to manage its ECS container environment. To remedy this, AWS introduced the Amazon Elastic Container Service for Kubernetes (Amazon EKS). With this new service, Kubernetes runs on AWS instead of, say, running on on-premises hardware. To note, this is an AWS-managed Kubernetes setup.

Amazon EKS runs the Kubernetes management infrastructure across multiple AWS availability zones, helping to eliminate a single point of failure. The service is fully compatible with Kubernetes, meaning you can use existing tools, applications, and plugins from the Kubernetes community and other sources that run on any standard Kubernetes environment.

Here’s how Amazon EKS works:

Provision an EKS cluster, after which the EKS automatically deploys Kubernetes master servers.
Deploy worker notes, adding them to your EKS cluster.
Connect to EKS by pointing your Kubernetes tooling at your EKS cluster.
Run Kubernetes applications by deploying them to your EKS cluster.
Benefits of Kubernetes for AWS include:

It offers high availability of master and worker nodes being spread across multiple availability zones.
You can upgrade, add or remove worker nodes.
It has automated version upgrades.
It has secure and encrypted communication channels automatically set up between nodes and managed control plane.
It supports hybrid OS deployments.
It integrates with some AWS services.
Drawbacks of Kubernetes on AWS. There are also several drawbacks to integrating Kubernetes with AWS:

It may not be as automated as AWS claims it to be. For example, creating clusters sometimes requires manual data entry from output produced from previous steps.
EKS considered difficult to set up and requires some technical background with containers.
