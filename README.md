My own implementation of Kubernetes microservices deployment, inspired by the [Google Cloud Platform microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo) project.  

## 🚀 Project Structure

```
k8s-microservices
├── README.md
└── base
    ├── ad
    │   ├── deployment.yaml
    │   └── service.yaml
    ├── cart
    │   ├── deployment.yaml
    │   └── service.yaml
    ├── checkout
    │   ├── deployment.yaml
    │   └── service.yaml
    ├── currency
    │   ├── deployment.yaml
    │   └── service.yaml
    ├── email
    │   ├── deployment.yaml
    │   └── service.yaml
    ├── frontend
    │   ├── deployment.yaml
    │   └── service.yaml
    ├── payment
    │   ├── deployment.yaml
    │   └── service.yaml
    ├── productcatalog
    │   ├── deployment.yaml
    │   └── service.yaml
    ├── recommendation
    │   ├── deployment.yaml
    │   └── service.yaml
    ├── redis
    │   ├── deployment.yaml
    │   └── service.yaml
    └── shipping
        ├── deployment.yaml
        └── service.yaml
```
## ⚙️ Presentation Layer
- **frontend**  

## ⚙️ Included Microservices
- **cartservice**  
- **checkoutservice**  
- **currencyservice**  
- **emailservice**  
- **paymentservice**  
- **productcatalogservice**  
- **recommendationservice**  
- **shippingservice**

Each microservice has its own Deployment + Service YAML in the base/ folder

## ⚙️ Supporting services
- **redis-cart** (in-memory cache for cartservice)

## 💻 Requirements

- [Minikube](https://minikube.sigs.k8s.io/docs/start/) or any Kubernetes cluster  
- `kubectl` CLI  
- Optional: Docker (if you want to build images locally)

## 🚀 Deploy Locally

1. Start Minikube:
```bash
minikube start
```
2. kubectl create namespace microservices
```bash
kubectl create namespace microservices
```

3. Apply all base manifests recursively:
```bash
kubectl apply -R -f ./base -n microservices
```

4. Verify deployments, services and pods
```bash
kubectl get deploy -n microservices
kubectl get svc -n microservices
kubectl get pod -n microservices
```

5. Access the frontend service
```bash
minikube service frontend -n microservices
```


---

### 🧹 Cleanup 

How to remove everything cleanly:

```bash
kubectl delete ns microservices
```
