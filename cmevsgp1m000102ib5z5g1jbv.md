---
title: "Kubernetes Architecture Explained: A Step-by-Step Guide for New Users"
seoTitle: "kubernetes "
datePublished: Thu Aug 28 2025 19:20:22 GMT+0000 (Coordinated Universal Time)
cuid: cmevsgp1m000102ib5z5g1jbv
slug: kubernetes-architecture-explained-a-step-by-step-guide-for-new-users
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1756408501083/77f5e652-6cb3-432a-8daf-bebd933029d2.png
tags: kubernetes, devops, containers, containerization, devops-articles, devops-journey, kubernetes-architecture, container-orchestration

---

Kubernetes (K8s) is an **open-source container orchestration platform**. It manages containerized applications across clusters of machines, handling deployment, scaling, networking, and updates. Without Kubernetes, running containers at scale quickly becomes chaotic—K8s brings automation and reliability.

---

## 🌟 Why Learn Kubernetes Architecture?

When running containers in production, challenges arise:

* Containers crash and must restart automatically.
    
* Applications need to scale up/down based on demand.
    
* Network traffic must be balanced between multiple replicas.
    
* Updates should happen without downtime.
    

Kubernetes addresses these through its architecture. Understanding the components will help you design, deploy, and debug systems effectively.

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1756408686520/4f0a2947-cd01-4a34-8bd7-09c46f484707.png align="center")

## 🧠 Control Plane (Cluster Brain)

The **Control Plane** is the decision-maker in Kubernetes. It manages the cluster and ensures that the system’s **desired state** (what you declare in YAML) matches the **actual state** (what’s running).

### 1\. **API Server** (`kube-apiserver`)

* Acts as the **front door** of the cluster.
    
* All commands (`kubectl`, dashboards, controllers, kubelets) go through it.
    
* Responsibilities:
    
    * **Authentication & Authorization** → validates user or component access.
        
    * **Validation** → checks YAML/JSON manifests for correctness.
        
    * **Admission Control** → enforces policies (quotas, security, limits).
        
    * **Persistence** → forwards cluster data to etcd.
        
* The API Server exposes the entire Kubernetes functionality as a REST API.
    

### 2\. **etcd**

* A **distributed key-value store** that acts as the cluster’s database.
    
* Stores all persistent cluster state:
    
    * Nodes in the cluster
        
    * Running pods
        
    * ConfigMaps, Secrets, Services
        
    * Desired vs actual workloads
        
* Highly available and fault-tolerant.
    
* Without etcd, Kubernetes would have no memory of what should exist.
    

### 3\. **Scheduler** (`kube-scheduler`)

* Watches for **unscheduled pods** (pods defined but not assigned to a node).
    
* Makes scheduling decisions based on:
    
    * Node resources (CPU, memory).
        
    * Node selectors and affinity/anti-affinity rules.
        
    * Taints and tolerations.
        
    * Pod priority and policies.
        
* The Scheduler doesn’t run containers itself; it only updates the API Server with pod → node assignments.
    

### 4\. **Controller Manager** (`kube-controller-manager`)

* Runs multiple controllers, each responsible for specific functions.
    
* A **controller** is a control loop that continuously checks the actual state against the desired state and takes corrective action.
    
* Examples:
    
    * **Node Controller** → monitors node health, reacts if a node goes down.
        
    * **ReplicaSet Controller** → ensures the correct number of pod replicas.
        
    * **Deployment Controller** → manages rolling updates and rollbacks.
        
    * **Endpoint Controller** → updates service endpoints as pods come and go.
        
* Controllers make Kubernetes **self-healing**.
    

### 5\. **Cloud Controller Manager** (optional)

* Runs only in cloud environments.
    
* Interfaces with cloud provider APIs (AWS, GCP, Azure).
    
* Handles tasks like:
    
    * Provisioning cloud load balancers.
        
    * Attaching persistent storage.
        
    * Managing cloud-based node lifecycle.
        

---

## 💪 Worker Nodes (Cluster Muscles)

Worker nodes are where your applications (Pods) actually run. Each worker node has the components required to execute workloads assigned by the Control Plane.

### 1\. **Kubelet**

* An agent that runs on every worker node.
    
* Communicates with the API Server.
    
* Receives PodSpecs (instructions) → starts pods via the container runtime.
    
* Continuously monitors running pods and reports status back to the Control Plane.
    
* Restarts failed containers to maintain desired state.
    

### 2\. **Container Runtime**

* The software responsible for actually running containers.
    
* Kubernetes supports multiple runtimes via the CRI (Container Runtime Interface).
    
* Common runtimes:
    
    * `containerd` (default in most distros)
        
    * `CRI-O`
        
    * Docker (deprecated as a runtime, but still widely known)
        
* Pulls images from registries and executes containers inside pods.
    

### 3\. **Kube-Proxy**

* Manages networking and load balancing.
    
* Implements Kubernetes **Service abstraction**:
    
    * Ensures pods within a Service can be reached consistently even if pod IPs change.
        
    * Distributes traffic between multiple pods.
        
* Works by configuring iptables or IPVS rules.
    

---

## 🔄 End-to-End Flow: How Kubernetes Works

Let’s trace what happens when you deploy an app:

1. **Developer applies a YAML file** (e.g., `kubectl apply -f app.yaml`).
    
2. **API Server** validates the request and stores the desired state in etcd.
    
3. **Controller Manager** detects the gap (desired pods vs. running pods) and requests pod creation.
    
4. **Scheduler** assigns the pods to suitable worker nodes.
    
5. **Kubelet** on those worker nodes picks up the PodSpec and instructs the container runtime to pull the image and start the container(s).
    
6. **Kube-Proxy** configures networking so traffic can reach the pods through Services.
    
7. **Feedback Loop**: Controllers continuously monitor actual vs desired state. If a pod fails, Kubernetes automatically replaces it (self-healing).
    

---

## 📊 Summary Table

| Component | Responsibility |
| --- | --- |
| **API Server** | Entry point, validation, persistence to etcd |
| **etcd** | Stores entire cluster state |
| **Scheduler** | Assigns pods to worker nodes |
| **Controller Manager** | Runs control loops to maintain desired state |
| **Kubelet** | Runs pods, monitors node & pod health |
| **Container Runtime** | Executes containers |
| **Kube-Proxy** | Configures networking and load balancing |

---

## ✅ Key Takeaways

* **Control Plane = Brain** → makes decisions and stores cluster state.
    
* **Worker Nodes = Muscles** → execute workloads and run containers.
    
* **Controllers = Autopilot** → keep actual state aligned with desired state.
    
* **etcd = Memory** → stores everything persistently.
    

Kubernetes is designed around separation of responsibilities. By understanding its architecture, you gain the ability to deploy, troubleshoot, and scale modern applications with confidence.