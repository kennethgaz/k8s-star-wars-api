# k8s-star-wars-api

Gerar imagem da API (precisa do Dockerfile e de uma conta no Docker Hub):
```sh
docker build -t kennethgaz/star-wars-api:1.0.1 .
docker push kennethgaz/star-wars-api:1.0.1
```

## Versão 1.0.0

```sh
sudo microk8s kubectl create deployment star-wars-api --image kennethgaz/star-wars-api:1.0.0
sudo microk8s kubectl get pods
sudo microk8s kubectl port-forward star-wars-api-5876d4dc4f-gdlg8 9000

curl http://localhost:9000/health

{"health":true,"version":"1.0.0"}
```

## Versão 1.0.1

```sh
sudo microk8s kubectl set image deployment star-wars-api star-wars-api=kennethgaz/star-wars-api:1.0.1
sudo microk8s kubectl get pods
sudo microk8s kubectl port-forward star-wars-api-55cfd99d46-htwsn 9000

curl http://localhost:9000/health

{"health":true,"version":"1.0.1"}
```
