\# 🐘 PostgreSQL + Adminer Stack



Entorno de base de datos relacional dockerizado para laboratorio local.



\## 📦 Servicios Incluidos

1\. \*\*PostgreSQL 15:\*\* Motor de base de datos robusto.

&nbsp;  - Datos persistentes en volumen `postgres\_data`.

2\. \*\*Adminer:\*\* Interfaz web ligera para gestionar la DB.

&nbsp;  - Accesible en: `http://IP-DEL-SERVIDOR:8080`



\## 🛠️ Despliegue

Para levantar el stack, usar Docker Compose (o Portainer Stacks):



```bash

docker-compose up -d

