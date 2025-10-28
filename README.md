# 🐱🐶 Kubernetes - Cats vs Dogs Voting App

Aplicação de exemplo usada em treinamentos de **Kubernetes**, que simula uma votação entre **gatos e cachorros**.  
O projeto demonstra na prática como funcionam **Deployments**, **Services**, **Pods** e a comunicação entre múltiplos containers dentro de um cluster.

---

## 🧩 Arquitetura da aplicação

A aplicação é composta por 5 serviços principais:

| Componente | Linguagem | Função |
|-------------|------------|--------|
| 🗳️ **vote** | Python | Frontend de votação (usuário vota em “gato” ou “cachorro”) |
| 📊 **result** | Node.js | Exibe o resultado da votação em tempo real |
| ⚙️ **worker** | .NET/C# | Processa votos e envia para o banco de dados |
| 💾 **db** | PostgreSQL | Armazena os votos |
| 🧠 **redis** | Redis | Fila de mensagens para os votos |

---

## 🚀 Pré-requisitos

Antes de rodar o projeto, verifique se você possui as seguintes ferramentas instaladas:

| Ferramenta | Versão mínima | Instalação |
|-------------|----------------|-------------|
| **Docker** | 20+ | [Instalar Docker](https://docs.docker.com/get-docker/) |
| **Kubectl** | 1.25+ | [Instalar Kubectl](https://kubernetes.io/docs/tasks/tools/) |
| **Minikube** | 1.31+ | [Instalar Minikube](https://minikube.sigs.k8s.io/docs/start/) |

---

## ⚙️ Instalação do Minikube

```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

# Testar
kubectl version --client
```

## Instalação do kubectl
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Testar instalação
minikube version
```

### 🧠 1. Iniciar o cluster

```bash
minikube start
````

O Minikube criará um cluster Kubernetes local com um nó virtualizado (usando Docker ou HyperKit no macOS).

### 🧩 2. Verificar o status

```bash
kubectl cluster-info
kubectl get nodes
```

Se o nó estiver com `STATUS: Ready`, o ambiente está pronto.

---

## 📦 Clonando o repositório

```bash
git clone https://github.com/MarcoBosc/catsVsDogs.git
ou 
git clone git@github.com:MarcoBosc/catsVsDogs.git
cd catsVsDogs
```

---

## 🧱 Estrutura do projeto

```
catsVsDogs/
│
├── vote/                  # Frontend de votação (Python)
├── result/                # Frontend de resultados (Node.js)
├── worker/                # Serviço de processamento (C#)
├── k8s-specifications/    # Manifests YAML do Kubernetes
├── docker-compose.yml     # Arquivo de exemplo para Docker Compose
└── README.md
```

---

## 🐳 Executando no Kubernetes

### 📥 1. Acesse a pasta com os manifests

```bash
cd k8s-specifications
```

### 🚀 2. Aplique todos os arquivos YAML

```bash
kubectl apply -f .
```

> Isso criará todos os Deployments e Services necessários para a aplicação (Redis, Postgres, Vote, Result, Worker).

---

## 🔍 3. Verificando os pods

```bash
kubectl get pods
```

Exemplo de saída esperada:

```
NAME                         READY   STATUS    RESTARTS   AGE
db-7d4b859db8-ptc4f          1/1     Running   0          1m
redis-7b7cb6d89c-7sk9l       1/1     Running   0          1m
vote-7d5fbbdbbf-c8t45        1/1     Running   0          1m
result-54d79bff64-kb2qt      1/1     Running   0          1m
worker-7c8f458cfd-vj9xz      1/1     Running   0          1m
```

---

## 🌐 4. Acessando a aplicação

Use o comando abaixo para abrir o serviço **de votação** no navegador:

```bash
minikube service vote
```

E o **serviço de resultados**:

```bash
minikube service result
```

> O Minikube abrirá automaticamente a URL do serviço no seu navegador padrão.

---

## 🧰 5. Comandos úteis

| Comando                      | Descrição                                 |
| ---------------------------- | ----------------------------------------- |
| `kubectl get all`            | Lista todos os recursos ativos no cluster |
| `kubectl logs <nome-do-pod>` | Exibe logs de um pod específico           |
| `kubectl delete -f .`        | Remove todos os recursos criados          |
| `kubectl get svc`            | Mostra os serviços e suas portas          |
| `minikube dashboard`         | Abre o painel visual do Kubernetes        |

---

## 🧹 6. Encerrando o ambiente

Quando terminar os testes, pare o cluster local:

```bash
minikube stop
```

Ou delete tudo completamente:

```bash
minikube delete
```

---

## 💡 Dica extra

Se quiser limpar todos os recursos criados pelo app (sem parar o cluster):

```bash
kubectl delete -f k8s-specifications/
```

---

## 🧠 Aprendizados com este projeto

Com este projeto você pratica:

* Deploys declarativos (YAML)
* Pods, Services e Deployments
* Comunicação entre containers
* Estratégia de *rolling update*
* Escalabilidade e replicação
* Monitoramento via `kubectl` e `dashboard`

---

## 📜 Referências oficiais

* [Repositório original – Docker Samples](https://github.com/dockersamples/example-voting-app)
* [Documentação oficial do Kubernetes](https://kubernetes.io/docs/home/)
* [Minikube Documentation](https://minikube.sigs.k8s.io/docs/start/)

---

Feito com 💙 para fins educacionais e laboratoriais.
Por Felipe Rodrigues, Luiz Menosso, Luiz Augusto, Eduardo, Marco Boschetti.

* [Repositório do projeto](https://github.com/MarcoBosc/catsVsDogs/)



#### Extra: Instalação do docker (caso não tiver)
```
# Atualizar pacotes
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common

# Adicionar chave do Docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Adicionar repositório Docker
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Instalar Docker
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io

# Adicionar seu usuário ao grupo docker (para rodar sem sudo)
sudo usermod -aG docker $USER
newgrp docker

# Testar
docker run hello-world
```
