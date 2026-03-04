<div align="center">

# 🐘 PostgreSQL + Adminer Stack — Beelink Home Server

<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
<img src="https://img.shields.io/badge/Adminer-34567C?style=for-the-badge&logo=adminer&logoColor=white"/>
<img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black"/>

**Entorno de base de datos relacional dockerizado para laboratorio local**

*PostgreSQL 15 + Adminer desplegados en servidor doméstico Beelink vía Docker Compose*

</div>

---

## 📦 Servicios del Stack

| Servicio | Imagen | Puerto | Descripción |
|:---|:---|:---|:---|
| **PostgreSQL 15** | `postgres:15` | `5432` | Motor de base de datos relacional |
| **Adminer** | `adminer` | `8080` | Interfaz web de gestión de la DB |

> Los datos de PostgreSQL persisten en el volumen `postgres_data` — sobreviven a reinicios y recreaciones del contenedor.

---

## 📸 Galería — Pruebas de Vida

**Contenedores activos en el servidor**

![Verificación contenedores](img/docker-ps.png)

**Conexión interna a PostgreSQL (CLI)**

![Conexión psql](img/psql-connection.png)

**Acceso web vía Adminer**

![Adminer web](img/adminer.png)

---

## 🚀 Despliegue

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) + [Docker Compose](https://docs.docker.com/compose/)
- Servidor Linux (local o remoto) — en este caso un **Beelink Mini PC**

### Levantar el stack
```bash
docker-compose up -d
```

### Verificar que está corriendo
```bash
docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
```

Deben aparecer **2 contenedores en verde**:

| Nombre | Estado esperado |
|:---|:---|
| `postgres-db` | Up X hours |
| `db-admin` | Up X hours |

---

## 🕵️ Guía de Verificación Manual

Pasos completos para reconectar y verificar el stack desde cero:

### 1. Conectar al servidor vía SSH
```bash
# Alias rápido
bee

# O comando completo
ssh heo@192.168.1.139
```

### 2. Comprobar contenedores activos
```bash
docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"
```

### 3. Conexión interna a PostgreSQL (CLI)
```bash
# Entrar en el contenedor
docker exec -it postgres-db psql -U heo -d heo_db
```

Una vez dentro del cliente `psql`:
```sql
-- Listar todas las bases de datos
\l

-- Listar tablas de la DB actual
\dt

-- Salir
\q
```

### 4. Acceso web vía Adminer
```
URL:        http://192.168.1.139:8080
Sistema:    PostgreSQL
Servidor:   postgres-db
Usuario:    heo
Base datos: heo_db
```

---

## 🏗️ Estructura del Repositorio
```
docker-postgres-stack/
├── docker-compose.yml      # Definición del stack completo
├── adminer.txt             # Credenciales de acceso (referencia local)
├── img/                    # Capturas de pantalla
└── README.md
```

---

## 🗺️ Roadmap

- [x] PostgreSQL 15 con persistencia de datos
- [x] Adminer como interfaz web de gestión
- [x] Acceso SSH desde terminal con alias `bee`
- [ ] Backup automático de la base de datos
- [ ] Conexión desde aplicaciones externas (ProfitBrain, SniperBot...)
- [ ] Integración en el stack de monitorización Grafana

---

## 🧑‍💻 Autor

**Héctor Oviedo** — Backend Developer & Home Lab Enthusiast

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/hectorob/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/HEO-80)

---

<div align="center">
  <sub>Desplegado en un <strong>Beelink Mini PC</strong> desde casa · Zaragoza, España 🏠</sub>
</div>
