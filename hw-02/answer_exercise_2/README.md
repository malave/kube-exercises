- ¿Cúal sería el comando que utilizarías para escalar el número de replicas a 10?
```shell script
 kubectl scale --replicas=10 rs/nginx-replicaset
```

- Si necesito tener una replica en cada uno de los nodos de Kubernetes, ¿qué objeto se adaptaría mejor? (No es necesario adjuntar el objeto)
Con un DaemonSet se asegura que todos o algunos de los nodos tengan corriendo na copia del Pod 