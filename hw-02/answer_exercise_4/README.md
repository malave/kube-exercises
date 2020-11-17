Primero se crea el deployment:
```shell script
kubectl apply -f deployment.yaml
```
Vemos que tiene la version `nginx:1.19.4`:

![describe-1](describe-1.png)

Y vemos el historial del rollout:
![history-1](history-1.png)

Luego actualizamos a la version `nginx:1.19.4-alpine`:
```shell script
kubectl set image deployment.apps/nginx-server nginx=nginx:1.19.4-alpine --record
```

Vemos que ahora tiene la version `nginx:1.19.4-alpine`:

![describe-1](describe-2.png)

Y vemos que en el historial del rollout hay un nuevo registro:

![history-2](history-2.png)

Por ultimo hacemos rollout undo hacia la version 1:

```shell script
kubectl rollout undo deployment.apps/nginx-server --to-revision=1
```

Vemos que ahora tiene otra vez la version `nginx:1.19.4`:

![describe-3](describe-3.png)

Y vemos que en el historial del rollout hay un nuevo registro:

![history-3](history-3.png)