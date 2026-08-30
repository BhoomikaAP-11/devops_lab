# 🚀 Kubernetes Getting Started — Exercise 1: Hello Pod

Deploying a containerized web app (nginx) on a local Kubernetes cluster using Minikube.

## 🧩 Business Problem (Zepto Example)

As a DevOps Engineer, deploy a lightweight web app (the storefront / delivery-status page) on Kubernetes so it is always running, portable, and can be scaled later. The `nginx` container image is used to simulate the storefront web app.

## 🛠️ Environment

- **OS:** Windows 11
- **Container runtime / driver:** Docker Desktop
- **Cluster:** Minikube v1.38.1
- **CLI:** kubectl v1.34.1

## 📋 Steps Performed

**1. Start a local Kubernetes cluster**
```bash
minikube start --driver=docker
```
Creates a single-node Kubernetes cluster running inside a Docker container.

**2. Deploy the app as a Pod (nginx)**
```bash
kubectl run hello-k8s --image=nginx --port=80
```
Runs the nginx image as a **Pod** named `hello-k8s`.

**3. Verify the Pod is running**
```bash
kubectl get pods
```
Output:
```
NAME        READY   STATUS    RESTARTS   AGE
hello-k8s   1/1     Running   0          40s
```

**4. Expose the Pod as a Service**
```bash
kubectl expose pod hello-k8s --type=NodePort --port=80
```
Creates a **NodePort Service** so the Pod is reachable from outside the cluster.

**5. Access the app in the browser**
```bash
minikube service hello-k8s
```
Opens the app in the browser — the **nginx welcome page** confirms the deployment.

## 📸 Output

**1. Terminal — cluster start, Pod creation, verification, Service, and tunnel:**

![Terminal output](./terminal-output.png)

**2. Browser — the nginx welcome page served from the Pod, confirming the app is deployed on Kubernetes:**

![nginx welcome page](./nginx-output.png)

## 🧠 Key Concepts Learned

- **Pod** — the smallest deployable unit in Kubernetes; wraps one (or more) containers.
- **Service (NodePort)** — gives the Pod a stable, reachable network endpoint.
- **Minikube** — runs a single-node Kubernetes cluster locally for learning and testing.
- **kubectl** — the command-line tool used to interact with the cluster.

## ✅ Result

Successfully deployed the nginx web app on Kubernetes, exposed it via a Service, and accessed it in the browser — completing Exercise 1.
