Habilitar Ingress
```shell script
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.41.2/deploy/static/provider/cloud/deploy.yaml
```
o
```shell script
minikube addons enable ingress

```

Agregar a `/etc/host` la siguiente linea
```shell script
127.0.0.1	luis.student.lasalle.com
```

Generamos un certificado:

```shell script
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout key.pem -out cert.pem -subj "/CN=luis.student.lasalle.com/O=luis.student.lasalle.com"
```

Y creamos un `Secret` con los certificados:

```shell script
kubectl create secret tls secret-tls --key key.pem --cert cert.pem
```

Aplicamos el deployment.yaml

```shell script
kubectl apply -f deployment.yaml
```

Probamos:

```shell script
curl --cacert cert.pem https://luis.student.lasalle.com/
```
