My own implementation of Kubernetes microservices deployment, inspired by the [Google Cloud Platform microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo) project. 

the project follows best practices: pinned image versions, liveness/readiness probes, resource requests and limits, Ingress instead of NodePort, and multiple replicas for reliability.

## 🚀 Project Structure
The project includes two deployment methods:
- kubectl deployment
- Helm deployment

Each deployment method is organized into its own folder which includes the following components:
- Microservices: individual services such as cart, checkout, adservice, etc.
- Frontend: the web application
- Redis: caching service

This structure allows for modular development, easy maintenance, and seamless deployment using either kubectl or Helm

## ⚙️ Components

### Presentation Layer
- **frontend**  

### Microservices
- **cartservice**  
- **checkoutservice**  
- **currencyservice**  
- **emailservice**  
- **paymentservice**  
- **productcatalogservice**  
- **recommendationservice**  
- **shippingservice**

### Supporting services
- **redis-cart** (in-memory cache for cartservice)

Each component has its own Deployment + Service YAML in the base/ folder

## 💻 Requirements

- [Minikube](https://minikube.sigs.k8s.io/docs/start/) or any Kubernetes cluster  
- `kubectl` CLI  
- Helm 3+ (for Helm deployments)
- Optional: Docker (if you want to build images locally)

## 🚀 Deploy Locally

### Using kubectl

1. Start Minikube
```bash
minikube start
```
2. kubectl create namespace microservices
```bash
kubectl apply -f ./base/namespace
```

3. Apply all base manifests recursively
```bash
kubectl apply -R -f ./base
```

4. Verify deployments, services and pods
```bash
kubectl get all -n microservices-demo
```

5. Access the frontend service
```bash
minikube service frontend -n microservices
```

### Using Helm
1. Install Helm chart into the same namespace
```bash
helm install microservices-demo ./helm/microservices-demo \
  --namespace microservices-demo \
  --create-namespace
```

2. Verify deployments, services and pods
```bash
kubectl get all -n microservices-demo
helm status microservices-demo -n microservices-demo
```

3. Access the frontend service
```bash
minikube service frontend -n microservices
```

---

## 🧹 Cleanup 

How to remove everything cleanly:
### Using kubectl
```bash
kubectl delete ns microservices
```

### Using Helm
```bash
helm uninstall microservices-demo -n microservices-demo
```
