# API DevOps - Tasks

API REST con Express + PostgreSQL, desplegada en Railway.

## Instalación

### 🐧 Ubuntu
\`\`\`bash
sudo apt update
sudo apt install -y nodejs npm postgresql-client
git clone <url-repo>
cd api-devops
npm install
cp .env.example .env   # completar con tu DATABASE_URL de Neon
npm run dev
\`\`\`

### 🪟 Windows (PowerShell)
\`\`\`powershell
# Requiere Node.js instalado desde https://nodejs.org
git clone <url-repo>
cd api-devops
npm install
copy .env.example .env   # completar con tu DATABASE_URL de Neon
npm run dev
\`\`\`

> En Windows, si usas WSL2, puedes seguir directamente los pasos de Ubuntu.

## Endpoints
- `GET /` — prueba
- `GET /health` — estado de la API y DB
- `GET /tasks` — listar tareas
- `POST /tasks` — crear tarea `{ "title": "string" }`

## Base de datos
PostgreSQL gestionado en [Neon](https://neon.tech).

## Despliegue
Railway (contenedor Docker). Deploy automático al hacer push a `main`.

## Backups
Ver `docs/backup-plan.md`.