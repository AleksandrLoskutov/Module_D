# Практикум: Задание D3.4

**Задание**
1. Создать Deployment со свойствами ниже:
- образ — _nginx:1.21.1-alpine;_
- имя — _nginx-sf;_
- количество реплик — _3._
___
- Развернул кластер на _minikube_. 
- Создал **deployment.yaml** с содержимым:
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

2. Создать конфигурационный файл для нашего приложения и поместить его в наш Pod со следующими свойствами:
- путь до файла в Pod’е — /etc/nginx/nginx.conf;
- содержимое файла (указано в конфиге).
___
- Создал **configmap.yaml** с содержимым:
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: nginx-config
data:
  nginx.conf: |
    user nginx;
    worker_processes  1;
    events {
      worker_connections  10240;
    }
    http {
      server {
          listen       80;
          server_name  localhost;
          location / {
            root   /usr/share/nginx/html;
            index  index.html index.htm;
          }
      }
    }
```
- Добавил в **deployment.yaml** следующую конфигурацию:
```
        volumeMounts:
        - name: config
          mountPath: "/etc/nginx"
          readOnly: true
      volumes:
      - name: config
        configMap:
          name: nginx-config
          items:
          - key: nginx.conf
            path: nginx.conf
```
