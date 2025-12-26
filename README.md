# 🐘 PostgreSQL + Adminer Stack

Entorno de base de datos relacional dockerizado para laboratorio local.

## 📦 Servicios Incluidos
1. **PostgreSQL 15:** Motor de base de datos robusto.
   - Datos persistentes en volumen `postgres_data`.
2. **Adminer:** Interfaz web ligera para gestionar la DB.
   - Accesible en: `http://IP-DEL-SERVIDOR:8080`

## 🛠️ Despliegue
Para levantar el stack, usar Docker Compose (o Portainer Stacks):

```bash
docker-compose up -d
📸 Galería de Despliegue (Pruebas de Vida)
1. Verificación de contenedores en el servidor
Comprobación vía terminal SSH de que los servicios están activos y escuchando.

2. Conexión interna a PostgreSQL
Acceso mediante CLI (psql) dentro del contenedor para verificar la creación de la base de datos heo_db.

3. Acceso Web vía Adminer
Interfaz gráfica en el puerto 8080 conectada correctamente al motor de base de datos.

🕵️‍♂️ Guía Rápida de Verificación
Pasos para reconectar y verificar el funcionamiento del stack manualmente:

1. Conexión al Servidor (SSH)
Abrir PowerShell y conectar al Beelink:

Bash

bee
# (O: ssh heo@192.168.1.139)
2. Comprobar estado de los contenedores
Verificar que postgres-db y db-admin están en estado "Up":

Bash

docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
3. Prueba de conexión interna (CLI)
Entrar en el contenedor de base de datos y listar las tablas:

Bash

docker exec -it postgres-db psql -U heo -d heo_db
# Una vez dentro, usar comando '\l' para listar DBs y '\q' para salir.
4. Acceso Visual (Adminer)
URL: http://192.168.1.139:8080

Sistema: PostgreSQL

Servidor: postgres-db

Usuario: heo

Contraseña: (Tu contraseña segura)

Base de datos: heo_db


---