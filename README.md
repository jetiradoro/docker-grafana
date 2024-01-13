# Stack de Grafana en Docker

Este repositorio contiene un stack de **Docker Compose** con los servicios de:

- **Grafana**: Servicio de monitorización visual con paneles de control dónde poder visualizar todas las métricas de las diferentes fuentes de datos
- **Prometheus**: Recolector de métricas para conectarse con las diferentes fuentes de datos
- **NODE_EXPORTER**: Agente de recolección de datos del estado del sistema, CPU, RAM, Discos, etc.
- **CADVISOR**: Agente de recolección de datos de los sistemas docker, servicios consumo de contenedores etc
- **LOKI**: Recolector de logs para suministrar la información centralizada a grafana

# Escenario

Este stack está pensado únicamente para fines de pruebas, ya que en un entorno real lo ideal sería tener los recolectores y Grafana en un servidor centralizado, y después los distintos agentes instalados en los sistemas externos que queramos monitorizar.

# Recursos y fuentes de información

He montado este stack basándome en varios tutoriales y videos que he encontrado por la red, os dejo el enlace a la lista de reproducción de **Caos Binario** desde dónde he estado siguiendo los inicios de como poner en marcha estos sistemas

- https://www.youtube.com/watch?v=PCJwJpbln6Q&list=PLC-jxfv-8E7L-w6bdX61qa4ehrrgCIh4R&ab_channel=CaosBinario

# Arrancar sistema

Las variables de entorno preparadas en el stack tienen una entrada `NET_EXTERNAL` y `GRAFANA DOMAIN` que en el caso de utilizar un reverse proxy se pueden setear con los datos necesarios para que el proxy responda a las peticiones.

Para arrancar el sistema:

1. Copiar el archivo **.env.example** a **.env** y rellenar las variables de entorno que necesitéis en vuestro ordenador.
2. Levantar el stack

```bash
docker-compose -f docker-compose.yml up -d
```

Para acceder a grafana se puede acceder a través de `http://localhost:9500` o el puerto de exposición que vosotros hayáis puesto en las variables de entorno
