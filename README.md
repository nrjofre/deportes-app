# Deportes app

## Despliegue

### Kubernetes

#### Deportes-api

Aplicar los comandos en el orden que se muestran.

Ejecutar desde el directorio `deportes-app-api`

 - ```minikube start```
 - ```minikube addons enable ingress```
 - ```kubectl apply -f k8s```
 - ```minikube tunnel```
    - este último commando permite hacer uso del servicio de manera local en `localhost:80` y la consola queda bloqueada, no debe ser cerrada mientras el servicio esté en uso.
    - Ocasionalmente el servicio de nginx ingress puede lanzar un error al iniciar el servicio, basta con volver a intentar lanzar el servicio un par de veces hasta que funcione.

#### Deportes-front

Ejecutar desde el directorio `deportes-app-front`

 - ```kubectl apply -f k8s```
 - ```minikube service deportesfront-service --url```