
# pucminas-guessgame-k8s

Projeto Kubernetes do Guess Game com backend Flask, frontend React e PostgreSQL.

---

## 🚀 Como rodar o projeto

### Via Helm Chart

1. Clone o repositório:

```bash
git clone https://github.com/viniciusaraujo20/pucminas-guessgame-k8s.git
cd pucminas-guessgame-k8s
```

2. Instale o Helm Chart no namespace `guessgame` (cria o namespace se não existir):

```bash
helm install guessgame ./helm-chart/ --namespace guessgame --create-namespace
```

3. Para abrir o frontend no Minikube, execute:

```bash
minikube service frontend -n guessgame
```

4. Se preferir acessar o frontend via `localhost`, use port-forward:

```bash
kubectl port-forward -n guessgame svc/frontend 8080:80
```

Acesse em: [http://localhost:8080](http://localhost:8080)

---

### Via aplicação direta dos manifests Kubernetes

1. Crie o namespace (caso não exista):

```bash
kubectl create namespace guessgame
```

2. Aplique todos os manifests da pasta `k8s/`:

```bash
kubectl apply -n guessgame -f k8s/
```

3. Para abrir o frontend no Minikube:

```bash
minikube service frontend -n guessgame
```

Ou via port-forward:

```bash
kubectl port-forward -n guessgame svc/frontend 8080:80
```

Acesse em: [http://localhost:8080](http://localhost:8080)

---

## 🛠️ Tecnologias usadas

- Kubernetes  
- Helm  
- Minikube  
- Flask (Backend Python)  
- React (Frontend)  
- PostgreSQL  
- NGINX (proxy reverso)  

---
## 📁 Estrutura do projeto

`guessgame-k8s/`  
├── `README.md`  
├── `k8s/`  
│   ├── `postgres-pvc.yaml`           # PersistentVolumeClaim para armazenamento do PostgreSQL  
│   ├── `postgres-deployment.yaml`    # Deployment do banco PostgreSQL  
│   ├── `backend-deployment.yaml`     # Deployment da API backend Flask  
│   ├── `backend-service.yaml`        # Service ClusterIP para expor o backend  
│   ├── `backend-hpa.yaml`            # Horizontal Pod Autoscaler para backend  
│   ├── `frontend-deployment.yaml`    # Deployment do frontend React com NGINX  
│   ├── `frontend-service.yaml`       # Service NodePort para expor o frontend  
├── `helm-chart/`  
│   ├── `Chart.yaml`                  # Metadata do Helm Chart  
│   ├── `values.yaml`                 # Valores configuráveis do Chart  
│   └── `templates/`                  # Templates dos manifests Kubernetes usados pelo Helm  
│       ├── `postgres-pvc.yaml`  
│       ├── `postgres-deployment.yaml`  
│       ├── `backend-deployment.yaml`  
│       ├── `backend-service.yaml`  
│       ├── `backend-hpa.yaml`  
│       ├── `frontend-deployment.yaml`  
│       ├── `frontend-service.yaml`  
