# Utilizando o template

## Aplicando

```bash
kubectl apply -f deployment.yaml
deployment.apps/conversao-temperatura created
service/conversao-temperatura created
```

## Verificando Pods

```bash
kubectl get pods

NAME                                     READY   STATUS    RESTARTS   AGE
conversao-temperatura-7469cd99d9-g2zvr   1/1     Running   0          48s
conversao-temperatura-7469cd99d9-h6667   1/1     Running   0          48s
```

## Verificando service

```bash
kubectl get svc

NAME                    TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
conversao-temperatura   LoadBalancer   10.111.36.204   <pending>     80:30989/TCP   65s
```

## Verificando all

```bash
kubectl get all

NAME                                         READY   STATUS    RESTARTS   AGE
pod/conversao-temperatura-7469cd99d9-g2zvr   1/1     Running   0          78s
pod/conversao-temperatura-7469cd99d9-h6667   1/1     Running   0          78s

NAME                            TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
service/conversao-temperatura   LoadBalancer   10.111.36.204   <pending>     80:30989/TCP   78s

NAME                                    READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/conversao-temperatura   2/2     2            2           78s

NAME                                               DESIRED   CURRENT   READY   AGE
replicaset.apps/conversao-temperatura-7469cd99d9   2         2         2       78s
```

## Removendo 

```bash

kubectl delete -f deployment.yaml
    deployment.apps "conversao-temperatura" deleted
    service "conversao-temperatura" deleted
```


kubectl port-forward 