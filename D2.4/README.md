# Практикум: Задание D2.4.1, Задание D2.4.2

**Задание D2.4.1**
___
- Поднял ВМ в Яндекс Облаке (**Ubuntu 22.04**)
- Установил _**docker**_:
  - _sudo curl -fsSL https://get.docker.com -o get-docker.sh
  - _sh get-docker.sh
  - sudo usermod -aG docker $USER
- Установил _**Minikube**_:
  - _curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
  - _sudo install minikube-linux-amd64 /usr/local/bin/minikube
- Запустил, указал количество нод - 5, имя - multinode-cluster
  - _minikube start --nodes 5 -p multinode-cluster 
