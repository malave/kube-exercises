Primero crear el ReplicaSet del ejemplo anterior [answer_exercise_2/replicaset.yaml](../answer_exercise_2/replicaset.yaml)
 
 Crea un objeto de tipo service para exponer la aplicación del ejercicio
anterior de las siguientes formas:
- Exponiendo el servicio hacia el exterior (crea [service1.yaml](service1.yaml))
```shell script
kubectl apply -f service1.yaml
```
Luego ir a http://localhost:31072/

- De forma interna, sin acceso desde el exterior (crea [service2.yaml](service2.yaml))

```shell script
kubectl apply -f service1.yaml
kubectl exec --stdin --tty rs/nginx-replicaset -- /bin/bash
curl nginx-replicaset-service2:80
```

- Abriendo un puerto especifico de la VM 
Con el fichero de [service1.yaml](service1.yaml) se abre un puerto especifico (31072 en este caso)
```shell script
kubectl apply -f service1.yaml
```
Luego ir a http://localhost:31072/