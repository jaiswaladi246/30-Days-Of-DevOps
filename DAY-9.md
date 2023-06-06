# DAY-9 | KUBERNETES PART-1

## Introduction to Kubernetes

Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. It provides a robust and flexible environment for running and managing container workloads.

## Key Concepts

### Containers

Containers are lightweight and isolated units that package an application and its dependencies, allowing for consistent and reproducible deployments across different environments.

### Cluster

A Kubernetes cluster consists of a set of nodes that host containerized applications. It acts as the underlying infrastructure where your applications run.

### Pods

Pods are the smallest and most basic unit in Kubernetes. They encapsulate one or more containers and share the same network namespace and storage volumes. Pods are scheduled onto nodes and are the building blocks of your application deployments.

### Services

Services provide a stable network endpoint to access a group of pods. They enable load balancing and service discovery within the cluster, allowing applications to communicate with each other.

### Replication Controllers and Replica Sets

Replication Controllers and Replica Sets ensure that a specified number of pod replicas are running at all times, helping to maintain the desired state of the application.

### Deployments

Deployments provide a higher-level abstraction for managing rolling updates and rollbacks of application deployments. They make it easier to define and manage the desired state of your application over time.

### ConfigMaps and Secrets

ConfigMaps and Secrets allow you to externalize configuration and sensitive information from your application containers. They provide a way to manage environment-specific settings without modifying the container images.

### Volumes

Volumes provide persistent storage for pods. They allow data to persist beyond the lifespan of a pod and enable data sharing between containers.

## Architecture

Kubernetes follows a master-worker architecture. The master components include the API server, controller manager, and scheduler, which collectively manage and control the cluster. The worker nodes, also known as minions, host the application workloads in the form of pods.
![alt text](https://github.com/jaiswaladi246/30-Days-Of-DevOps/blob/main/Images/8.png?raw=true)

### MASTER NODE

1. **API Server**: The API server is the central component of the Kubernetes control plane. It acts as the primary interface for users, administrators, and other components to interact with the cluster. It exposes the Kubernetes API, which allows users to create, update, and delete Kubernetes objects such as pods, services, deployments, and more. The API server handles authentication, authorization, and validation of API requests, ensuring the cluster's security and consistency.

2. **Scheduler**: The scheduler is responsible for placing pods onto nodes in the cluster. It evaluates various factors such as resource requirements, node availability, and constraints defined in the pod specification. The scheduler makes intelligent decisions to optimize resource utilization and ensure that pods are scheduled on suitable nodes. It continuously monitors the cluster state and adjusts the pod assignments as needed.

3. **Controller Manager**: The controller manager is a collection of controllers that manage different aspects of the cluster. Each controller focuses on maintaining a specific desired state and performs tasks to reconcile the current state with the desired state. Some examples of controllers include the Replication Controller, Replica Set Controller, Deployment Controller, StatefulSet Controller, and Service Account and Token Controller. The controller manager continuously monitors the cluster's state and takes corrective actions to ensure that the desired state is achieved and maintained.

4. **etcd**: etcd is an open-source distributed key-value store that acts as the Kubernetes cluster's primary datastore. It stores and retrieves configuration data, state information, and metadata of all Kubernetes objects in a reliable and distributed manner. The API server, scheduler, controller manager, and other components interact with etcd to read and write the cluster's state. etcd provides high availability and consistency by using a distributed consensus algorithm and ensures that the cluster operates reliably even in the presence of failures.

In summary, the API server acts as the entry point for interacting with the cluster, the scheduler places pods onto nodes, the controller manager manages various controllers to maintain the desired state, and etcd serves as the distributed datastore for the cluster's configuration and state information. Together, these components form the core control plane of a Kubernetes cluster, enabling the management and orchestration of containerized applications at scale.

### AGENT NODE

Here's an explanation of container runtime, kubelet, and kube-proxy in Kubernetes:

1. **Container Runtime**: The container runtime is responsible for running and managing containers on each node in the Kubernetes cluster. It interacts directly with the underlying operating system's kernel to start, stop, and monitor containers. Kubernetes supports multiple container runtimes, such as Docker, containerd, and CRI-O. The container runtime ensures that containers are isolated from each other, have the required resources, and can communicate with other containers and the outside world.

2. **Kubelet**: The kubelet is an agent that runs on each node in the Kubernetes cluster. It is responsible for managing and maintaining the state of the node and its associated containers. The kubelet communicates with the control plane components, such as the API server and the scheduler, to receive instructions and report the node's status. It ensures that the containers specified in the pod manifests are running and healthy by starting, stopping, and monitoring them. The kubelet also handles tasks like attaching and mounting volumes, performing health checks, and logging container status.

3. **kube-proxy**: kube-proxy is a network proxy that runs on each node in the Kubernetes cluster. It enables network communication between services or pods inside the cluster. kube-proxy maintains network rules (iptables or IPVS rules) to route traffic to the appropriate destination based on the service or pod IP address and port. It handles load balancing across multiple pod replicas of a service, provides service discovery, and handles network address translation (NAT) for pods accessing services from outside the cluster. kube-proxy ensures that the network connections within the cluster are properly managed and routed.

In summary, the container runtime manages containers on each node, the kubelet is responsible for managing the node and its containers, and kube-proxy facilitates network communication and load balancing among pods and services within the cluster. These components work together to ensure that containers are running, properly networked, and can communicate with each other in a Kubernetes cluster.


## Benefits of Kubernetes

- **Scalability:** Kubernetes scales applications horizontally by adding or removing pod replicas based on demand.
- **High Availability:** It provides built-in mechanisms to ensure that your applications are highly available by distributing them across multiple nodes.
- **Self-Healing:** Kubernetes automatically restarts failed containers and replaces unhealthy pods, ensuring the desired state is maintained.
- **Rolling Updates and Rollbacks:** Deployments enable seamless rolling updates of application versions and facilitate easy rollbacks in case of issues.
- **Service Discovery and Load Balancing:** Kubernetes services allow applications to discover and communicate with each other, distributing traffic evenly across pods


**YAML Files for Kubernetes:**

YAML (YAML Ain't Markup Language) is a human-readable data serialization format commonly used for defining configurations in Kubernetes. YAML files are used to describe the desired state of Kubernetes objects, such as pods, services, deployments, and more. They follow a hierarchical structure with key-value pairs and indentation to define the properties and values of each object.

Here's an example of a YAML file defining a simple Kubernetes pod:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: nginx:latest
    ports:
    - containerPort: 80
```

In this example:
- `apiVersion` specifies the Kubernetes API version being used.
- `kind` defines the type of Kubernetes object being created (in this case, a pod).
- `metadata` contains information about the pod, such as its name.
- `spec` specifies the desired state of the pod.
- `containers` defines the list of containers running within the pod.
- `name` specifies the name of the container.
- `image` specifies the container image to be used.
- `ports` defines the list of ports to be exposed by the container.



```markdown
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: nginx:latest
    ports:
    - containerPort: 80
```
```
```

You can now copy and paste the above content into your Markdown file on GitHub. The YAML code block is enclosed in triple backticks (```) with `yaml` specified after the opening triple backticks to specify the language for syntax highlighting.

Note: The Markdown formatting might not be rendered correctly in this text-based interface, but it should appear correctly in the actual Markdown file on GitHub.
