Se crean los deployments de `blue` y `green`. 
- Blue -> `nginx:1.19.4`
- Green -> `nginx:1.19.3`

```shell script
kubectl apply -f deploy-blue.yaml 
kubectl apply -f deploy-green.yaml 
```

Luego se crea un servicio que por defecto va a apuntar a `blue` en el puerto `3107`
```shell script
kubectl apply -f service.yaml 
```

En una terminar aparte se puede correr el siguiente commando para ver la version de nginx y ver que version está corriendo en ese momento:

```shell script
while true; do curl -s http://localhost:31072/version | grep nginx; sleep 0.5; done
```

Para cambiar de `blue` a `green` se puede modificar el `server.yaml` y luego volver a correr el comando:

```shell script
kubectl apply -f service.yaml 
```

O también se puede correr el siguiente comando desde la terminal:

```shell script
kubectl patch service nginx-service  -p '{"spec":{"selector":{"role": "green"}}}'
```