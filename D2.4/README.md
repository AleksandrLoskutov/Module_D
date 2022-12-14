# Практикум: Задание D2.4.1, Задание D2.4.2

**Задание D2.4.1**
___
- Поднял ВМ в Яндекс Облаке (**Ubuntu 22.04**)
- Установил _**docker**_:
  - _sudo curl -fsSL https://get.docker.com -o get-docker.sh_
  - _sh get-docker.sh_
  - _sudo usermod -aG docker $USER_
- Установил _**Minikube**_:
  - _curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64_
  - _sudo install minikube-linux-amd64 /usr/local/bin/minikube_
- Запустил, указал количество нод - 5, имя - multinode-cluster:
  - _minikube start --nodes 5 -p multinode-cluster_
- Установил _**kubectl**_:
  - _sudo snap install kubectl --classic_
___
**Результаты выполнения команд**
- _kubectl get nodes_ - количество нод в кластере
- ![minicube-nodes](./images/minicube-nodes.PNG)
- _minikube status -p multinode-cluster_ - статус кластера
- ![minicube-status](./images/minicube-status.PNG)
___

**Задание D2.4.2**
___
**Описание:**

Сообщество Kubernetes объявило, что в конце 2021 года Docker в качестве среды выполнения контейнеров будет объявлен как устаревший и не будет использоваться в K8S-кластере. Но Kind, который поднимает K8S-кластер на Docker, говорит о том, что в отношении поддержки работы кластера K8S беспокоиться не стоит.

**Задание:**

Почему Kind говорит, что это изменение его не затронет?

**Ответ:**

**Kind** — это инструмент для запуска локальных кластеров Kubernetes с помощью "узлов" контейнера Docker, а изменения в Kubernetes связаны именно с внутренней средой выполнения контейнеров и не затрагивают внешние инструменты.


