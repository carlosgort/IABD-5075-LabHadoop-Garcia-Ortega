\# Práctica de Laboratorio: Clúster Multi-Nodo Apache Hadoop 3



Despliegue como código (IaC) de un clúster distribuido \*\*Apache Hadoop 3\*\* sobre Docker, auditoría de bloques en HDFS, simulación de tolerancia a fallos y ejecución de procesamiento distribuido MapReduce sobre YARN.



\## Arquitectura Desplegada



| Componente | Contenedor | Rol en el clúster | Interfaz / Puerto |

| :--- | :--- | :--- | :--- |

| \*\*HDFS NameNode\*\* | `namenode` | Gestión de metadatos y espacio de nombres | `http://localhost:9870` |

| \*\*HDFS DataNode 1\*\* | `datanode1` | Almacenamiento físico de bloques | Interno (`9866`) |

| \*\*HDFS DataNode 2\*\* | `datanode2` | Almacenamiento físico de bloques | Interno (`9866`) |

| \*\*HDFS DataNode 3\*\* | `datanode3` | Almacenamiento físico de bloques | Interno (`9866`) |

| \*\*YARN ResourceManager\*\* | `resourcemanager` | Planificación global de recursos | `http://localhost:8088` |

| \*\*YARN NodeManager\*\* | `nodemanager` | Ejecución de contenedores MapReduce | Interno (`8042`) |



\### Parámetros de almacenamiento configurados

\- \*\*Imagen base:\*\* `apache/hadoop:3`

\- \*\*Tamaño de bloque (`dfs.blocksize`):\*\* `64 MiB` (`67108864` bytes)

\- \*\*Factor de replicación (`dfs.replication`):\*\* `2`



\## Instrucciones de Arranque y Parada



1\. \*\*Desplegar el clúster:\*\*

&#x20;  ```bash

&#x20;  cd docker

&#x20;  docker compose up -d

&#x20;  ```

2\. \*\*Acceder al nodo maestro:\*\*

&#x20;  ```bash

&#x20;  docker exec -it namenode bash

&#x20;  ```

3\. \*\*Detener el clúster y liberar volúmenes:\*\*

&#x20;  ```bash

&#x20;  cd docker

&#x20;  docker compose down -v

&#x20;  ```



\## Estructura del Repositorio



\- `docker/`: Definición de infraestructura como código (`docker-compose.yml` y `config`).

\- `evidencias/`: Capturas de pantalla de la auditoría HDFS, simulación de caída de nodo y ejecución en YARN.

\- `informe/`: Memoria técnica de la práctica en formato PDF.



\## Autoría



\- \*\*Alumno:\*\* Carlos García Ortega

\- \*\*Módulo:\*\* Sistemas de Big Data (IABD - 5075 / RD 279/2021)

