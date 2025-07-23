
# pucminas-guessgame-k8s

Projeto Kubernetes do Guess Game com backend Flask, frontend React e PostgreSQL.

---

## 🚀 Como rodar o projeto

### Via Helm Chart

1. Clone o repositório:

```bash
git clone https://github.com/seu-usuario/pucminas-guessgame-k8s.git
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
- NGINX (proxy reverso e balanceador)  

---

## 📁 Estrutura do projeto

- `helm-chart/` — Chart Helm para deploy no Kubernetes  
- `k8s/` — Manifests Kubernetes para deploy manual  
- `README.md` — Documentação do projeto
