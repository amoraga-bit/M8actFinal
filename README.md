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

## 🌐 API en producción

**URL base:** https://actfinalm8-production.up.railway.app

### Prueba rápida (GET, funciona directo en el navegador)

- Endpoint de prueba: https://actfinalm8-production.up.railway.app/
- Estado de salud (monitoreo): https://actfinalm8-production.up.railway.app/health
- Listar tareas: https://actfinalm8-production.up.railway.app/tasks

### Crear una tarea (POST)

\`\`\`bash
curl -X POST https://actfinalm8-production.up.railway.app/tasks \
  -H "Content-Type: application/json" \
  -d '{"title": "Nueva tarea de prueba"}'
\`\`\`

O con HTTPie:
\`\`\`bash
http POST https://actfinalm8-production.up.railway.app/tasks title="Nueva tarea de prueba"
\`\`\`

## Base de datos
PostgreSQL gestionado en [Neon](https://neon.tech).

## Despliegue
Railway (contenedor Docker). Deploy automático al hacer push a `main`.

## Backups
Ver `docs/backup-plan.md`.