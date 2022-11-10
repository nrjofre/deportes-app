# Deportes app

- [Deportes app](#deportes-app)
  - [Despliegue](#despliegue)
    - [Deportes-api](#deportes-api)
      - [Colecciones de postman para probar la API](#colecciones-de-postman-para-probar-la-api)
    - [Deportes-front](#deportes-front)
    - [Opensearch](#opensearch)

## Despliegue

### Deportes-api

Aplicar los comandos en el orden que se muestran.

Ejecutar desde el directorio `deportes-app-api`

- ```console
   minikube start
  ```
- ```console
   minikube addons enable ingress
  ```
- ```console
   kubectl apply -f k8s
  ```
- ```console
   minikube tunnel
  ```
  - este último commando permite hacer uso del servicio de manera local en `localhost:80` y la consola queda bloqueada, no debe ser cerrada mientras el servicio esté en uso.
  - Ocasionalmente el servicio de nginx ingress puede lanzar un error al iniciar el servicio, basta con volver a intentar lanzar el servicio un par de veces hasta que funcione.

#### Colecciones de postman para probar la API

- [Endpoints de user](https://www.getpostman.com/collections/50bb202d41ed5591f7ef)
- [Endpoints de football data](https://www.getpostman.com/collections/237603016ca018f54b0e)
- [Endpoints de NBA data](https://www.getpostman.com/collections/f6e0dbeec7c76e1040cd)

### Deportes-front

Ejecutar desde el directorio `deportes-app-front`

- ```console
   kubectl apply -f k8s
  ```
- ```console
   minikube service deportesfront-service --url
  ```
  - al igual que usando ingress, aquí se expone el frontend en el puerto que nos entregará el ejecutar este comando. La consola quedará bloqueada, no cerrar mientras dura el programa.

### Opensearch

Ejecutar desde el directorio `localopensearch`

- ```console
   docker compose up
  ```

IMPORTANTE: dependiendo de la cantidad de memoria asiganda para el uso de dockers puede tirar error, para solucionar esto hay que incrementar la cantidad de memoria:

- Sistemas operativos basados en linux: se puede configurar directamente en Docker Desktop.
- Windows:
  1.  Abrir una consola de WSL2.
  2.  ejecutar el comando: `cd/etc`
  3.  ejectuar el comando `sudo vim sysctl.conf`
  4.  Se abrira un archivo en la consola, ir hasta la última línea y escribir: `vm.max_map_count=262144`
  5.  Para cerrar y guardar los cambios escribir: `:x`
  6.  Actualizar el nuevo valor de memoria ejectuando: `sudo sysctl -p`
