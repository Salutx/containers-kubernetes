# Como rodar Apache e Nginx no Minikube - Passo a Passo Rápido

---

## 1. Inicie o Minikube

```bash
minikube start

eval $(minikube docker-env)

docker build -t apache-custom:v2 -f ./.composes/apache/Dockerfile-apache ./.composes/apache
docker build -t nginx-custom:v2 -f ./.composes/nginx/Dockerfile-nginx ./.composes/nginx

minikube kubectl -- apply -f ./apache-deployment.yaml
minikube kubectl -- apply -f ./nginx-deployment.yaml

minikube kubectl -- get pods
minikube kubectl -- get services

minikube service apache-service --url
minikube service nginx-service --url
```

Para parar o minikube:
```bash
minikube stop
```
