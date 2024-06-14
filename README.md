# projetos-helm

## Listando os projetos

```bash
helm list

NAME    NAMESPACE       REVISION        UPDATED STATUS  CHART   APP VERSION
```

## Criando o projeto do chart

```bash
helm create [nome do projeto]

helm create webapp-node
```

## Validando o Chart

```bash

helm install [nome da release] ./webapp-node/ --debug --dry-run

helm install webapp ./webapp-node/ --debug --dry-run

install.go:222: [debug] Original chart version: ""
install.go:239: [debug] CHART PATH: /home/rfahham/projetos/projetos-helm/webapp-node

NAME: webapp
LAST DEPLOYED: Thu Jun 13 21:11:13 2024
NAMESPACE: workon
STATUS: pending-install
REVISION: 1
TEST SUITE: None
USER-SUPPLIED VALUES:
{}

COMPUTED VALUES:
app:
  containerPort: 80
  image:
    repository: nginx
    tag: latest
  replicas: 2

HOOKS:
MANIFEST:
---
# Source: webapp-node/templates/deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
spec:
  selector:
    matchLabels:
      app: webapp
  replicas: 2
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: webapp
        image: nginx:latest
        ports:
        - containerPort: 80

NOTES:
```

## Redirecionando o output para um arquivo de debug

```bash
helm install webapp ./webapp-node/ --debug --dry-run > debug.yaml
```

## Para deployar

```bash
helm install webapp ./webapp-node/
```

## Fazer atualização

Criar um arquivo chamado setup.values.yaml e fazer as alterações

```bash
helm upgrade werapp ./webapp-node/ --values=setup.values.yaml
```

## No caso de algum erro de imagem por exemplço

```bash
helm roollback [nome da release] e a versão que estava funcionando 1
```

## Desinstalar as releases

```bash
helm unistall [nome da release]
```

