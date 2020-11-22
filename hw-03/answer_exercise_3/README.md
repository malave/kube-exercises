Aplicamos las configuraciones
```shell script
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f hpa.yaml
```
Creamos una prueba de carga:

```shell script
kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.0000000001; do wget -q -O- http://nginx-service; done"
```

Revisamos el estado de hpa:

```shell script
kubectl get hpa nginx-hpa
```
