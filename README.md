# Nerdearla - Integrando el mundo con Kafka & Friends

Proyecto destinado a contener el material para ejecutar el workshop dictado para Nerdearla.  

## Requisitos

- IDE de Base de datos : [DBeaver](https://dbeaver.io/download/) 
- "IDE" para API :[Postman ](https://www.postman.com/downloads/) o cURL o [swagger online](https://editor.swagger.io) utilizando el oas adjunto.
- [Docker](https://docs.docker.com/desktop) // [Podman](https://podman.io/getting-started/installation)
- [Docker-compose](https://docs.docker.com/compose/install/) //  [Podma-compose](https://github.com/containers/podman-compose)
- [Drivers JDBC Confluent](https://docs.confluent.io/kafka-connect-jdbc/current/index.html), incluye fat jar
- Google PubSub 
- [Rabbit MQ Connector](https://github.com/jonahharris/kafka-connect-rabbitmq)
[Proyecto](https://github.com/GoogleCloudPlatform/pubsub.git), incluye [fat Jar](https://github.com/GoogleCloudPlatform/pubsub/releases) 


## Overview

Este proyecto contiene todo lo requerido para montar localmente 
- broker kafka
- Instancia de kafka Connect Distribuida
- Crear connectores JDBC , GCP y RabbitMQ
- Instancia de BD MSSQL Server 2017
- Instancias de observabilidad.
    * Grafana
    * Jaeger
    * Promtail + Loki

## disclaimer
El workshop no incluye ejemplos de funcionamiento de Kafka Connect, los ejemplos son implementados en el workshop.

## Uso

Para inicializar los contenedores pueden usar docker o podman, los comandos son los mismos.

```
docker-compose up -d
```
```
podman-compose up -d
```

* Linux : deben desactivar SElinux y ejecutar con su/sudo
    *   ```
        sudo setenforce 0 
        ```

## Commandos recurrentes.

Para podman, deben cambiar "docker-compose" -> "podman" 

### Todos los contenedores : Inicio / detencion + eliminacion 
```
docker-compose up -d
```
```
docker-compose down
```

### Conexion a un contenedor
```
docker exec -it EL_CONTENEDOR bin/bash
```

### Consumo
```
docker-compose exec broker kafka-console-consumer --topic EL_TOPIC --bootstrap-server broker:9091 --from-beginning
```

### Produccion
```
docker-compose exec broker kafka-console-producer --topic EL_TOPIC --broker-list localhost:9091
```