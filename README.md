Perfeito, Marco 👏
Aqui vai um **README.md completo, limpo e profissional**, cobrindo **desde a instalação do Minikube até a execução do projeto “Cats vs Dogs”** (a *Example Voting App* usada em cursos de Kubernetes).
Você pode colocar esse arquivo na raiz do projeto (`example-voting-app/README.md`).

---

````markdown
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
git clone https://github.com/dockersamples/example-voting-app.git
cd example-voting-app
```

---

## 🧱 Estrutura do projeto

```
example-voting-app/
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
Por [Marco Antônio Boschetti](https://github.com/marcoboschetti).

```

---

Quer que eu adicione uma **seção bônus com comandos de troubleshooting** (ex: pods com erro, reinício de rollout, logs detalhados etc.) no final do README também? Isso deixaria o guia bem completo pra uso em aula ou laboratório.
```
Perfeito, Marco 👏
Aqui vai um **README.md completo, limpo e profissional**, cobrindo **desde a instalação do Minikube até a execução do projeto “Cats vs Dogs”** (a *Example Voting App* usada em cursos de Kubernetes).
Você pode colocar esse arquivo na raiz do projeto (`example-voting-app/README.md`).

---

````markdown
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
git clone https://github.com/dockersamples/example-voting-app.git
cd example-voting-app
```

---

## 🧱 Estrutura do projeto

```
example-voting-app/
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
Por [Marco Antônio Boschetti](https://github.com/marcoboschetti).

```

---

Quer que eu adicione uma **seção bônus com comandos de troubleshooting** (ex: pods com erro, reinício de rollout, logs detalhados etc.) no final do README também? Isso deixaria o guia bem completo pra uso em aula ou laboratório.
```
