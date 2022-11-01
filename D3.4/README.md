# Практикум: Задание D3.4

**Задание**
1. Создать Deployment со свойствами ниже:
- образ — _nginx:1.21.1-alpine;_
- имя — _nginx-sf;_
- количество реплик — _3._
___
- Развернул кластер на _minikube_. 
- Создал deployment.yaml с содержимым:
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-sf
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.21.1-alpine
        ports:
        - containerPort: 80
```
- Применил конфиг с помощью команды - _kubectl apply -f deployment.yaml_
- ![deployment_k8s](./images/deployment_k8s.PNG)
___

