# DAY-9 | KUBERNETES PART-1 & PART-2

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

Certainly! Here's an explanation of Deployment and Service YAML files for Kubernetes, along with examples, and the generated output in Markdown format for GitHub:

**Deployment YAML Files:**

Deployment YAML files in Kubernetes are used to define and manage a set of identical pods. They ensure that a specified number of pod replicas are running and handle rolling updates and rollbacks. Deployments provide declarative updates for pods and are widely used for managing stateless applications.

Here's an example of a Deployment YAML file:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: nginx:latest
        ports:
        - containerPort: 80
```

In this example:
- `apiVersion` specifies the Kubernetes API version being used.
- `kind` defines the type of Kubernetes object being created (in this case, a Deployment).
- `metadata` contains information about the Deployment, such as its name.
- `spec` specifies the desired state of the Deployment.
- `replicas` defines the desired number of pod replicas.
- `selector` is used to match the pods controlled by the Deployment.
- `template` defines the pod template used to create the replicas.
- `containers` specifies the list of containers running within the pod template.

**Service YAML Files:**

Service YAML files in Kubernetes are used to define a stable endpoint for accessing a group of pods. Services enable load balancing and service discovery within the cluster. They provide an abstraction layer that allows pods to be replaced or scaled without affecting the application's accessibility.

Here's an example of a Service YAML file:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
  type: NodePort
```

In this example:
- `apiVersion` specifies the Kubernetes API version being used.
- `kind` defines the type of Kubernetes object being created (in this case, a Service).
- `metadata` contains information about the Service, such as its name.
- `spec` specifies the desired state of the Service.
- `selector` is used to match the pods that the Service will target.
- `ports` defines the list of ports to be exposed by the Service.
- `protocol` specifies the protocol to be used (in this case, TCP).
- `port` specifies the port number for accessing the Service.
- `targetPort` specifies the port number on the pods to which traffic should be forwarded.
- `type` defines the type of Service. `NodePort` exposes a service externally to the cluster by means of the target nodes IP address and the NodePort.


## --- KUBERNETES Install Steps ---
```markdown


## Step1:

### On Master and slave


apt-get update -y
apt-get install docker.io -y
service docker restart
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" >/etc/apt/sources.list.d/kubernetes.list
apt-get update
apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y
```

## Step2:

### On Master node:

```bash
kubeadm init --pod-network-cidr=192.168.0.0/16
```

## Step3:

### On Master node:

```bash
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

## Step4:

### On Master node:

```bash
kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.1/manifests/calico.yaml
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.49.0/deploy/static/provider/baremetal/deploy.yaml
```


### Kubectl is a command-line tool used to interact with Kubernetes clusters. It allows you to deploy and manage applications, inspect and modify cluster resources, and perform various administrative tasks. Here are some basic kubectl commands:

1. **kubectl get**: Retrieve information about resources in the cluster.
   - `kubectl get pods`: List all pods in the cluster.
   - `kubectl get deployments`: List all deployments in the cluster.
   - `kubectl get services`: List all services in the cluster.
   - `kubectl get nodes`: List all nodes in the cluster.

2. **kubectl describe**: Get detailed information about a specific resource.
   - `kubectl describe pod <pod-name>`: Show detailed information about a specific pod.
   - `kubectl describe deployment <deployment-name>`: Show detailed information about a specific deployment.
   - `kubectl describe service <service-name>`: Show detailed information about a specific service.

3. **kubectl create**: Create a resource from a file or inline definition.
   - `kubectl create -f <file.yaml>`: Create a resource defined in a YAML file.
   - `kubectl create deployment <deployment-name> --image=<image-name>`: Create a deployment from a specified container image.

4. **kubectl delete**: Delete a resource.
   - `kubectl delete pod <pod-name>`: Delete a specific pod.
   - `kubectl delete deployment <deployment-name>`: Delete a specific deployment.
   - `kubectl delete service <service-name>`: Delete a specific service.

5. **kubectl apply**: Apply changes to a resource.
   - `kubectl apply -f <file.yaml>`: Apply changes to a resource defined in a YAML file.
   - `kubectl apply -f <dir>`: Apply changes to all resources defined in a directory.

6. **kubectl logs**: View the logs of a pod.
   - `kubectl logs <pod-name>`: Print the logs of a specific pod.

7. **kubectl exec**: Execute a command inside a container of a pod.
   - `kubectl exec -it <pod-name> -- <command>`: Run an interactive shell in a specific pod.

8. **kubectl port-forward**: Forward local ports to a pod.
   - `kubectl port-forward <pod-name> <local-port>:<pod-port>`: Forward a local port to a specific pod.

These are just a few examples of the most commonly used kubectl commands. There are many more commands available, and you can explore additional options and parameters in the Kubernetes documentation or by using `kubectl --help`.

