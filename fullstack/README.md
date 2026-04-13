Estructura
Plaintext

fullstack/
  backend/
    app.js
    server.js
    config/
      db.js
    controllers/
      tasksController.js
    middlewares/
      taskValidation.js
    routes/
      taskRoutes.js
  frontend/
    app.js
    index.html
  .env
  package.json
  README.md

Stack

    Backend: Node.js (CommonJS) + Express

    Database: MySQL (Hosted on Railway)

    Frontend: Bootstrap 5 + Vanilla JS

    Deploy: Vercel (Frontend) & Railway (Backend/DB)

    Herramientas: dotenv, CORS, mysql2

Features

    Gestión  Crear, listar, editar y eliminar tareas.

    Almacenamiento: Datos alojados en instancia de MySQL en Railway.

    Validaciones: Protección de integridad de datos en ambos extremos (Client/Server).

    UI/UX: Notificaciones tipo Toast y diseño responsivo con Bootstrap.

    CORS Configurado: Comunicación segura entre dominios de Vercel y Railway.

Configuración de Entorno (.env)

Crea un archivo .env en la raíz para desarrollo local:
Fragmento de código

# Database Config
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=admin123
DB_NAME=task_manager

DATABASE_URL=mysql://user:pass@host:port/db

Despliegue (Deployment)
1. Backend & Database (Railway)

    Crea un nuevo proyecto en Railway y añade un servicio de MySQL.

    Despliega la carpeta backend/.

    Configura las Variables de Entorno en el dashboard de Railway:

        PORT: 3000 (o el que use tu servidor)

        DATABASE_URL: Generada automáticamente por Railway.

2. Frontend (Vercel)

    Conecta tu repositorio a Vercel.

    Configura el Root Directory como frontend/.

    Añade la variable de entorno:

        API_URL: https://projectu4.railway.app).

Base de Datos

Ejecuta el siguiente script en tu instancia de Railway (Query Editor):
SQL

CREATE TABLE IF NOT EXISTS tasks (
  id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  priority ENUM('Low', 'Medium', 'High') NOT NULL,
  isCompleted BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

Instalación Local

    Clonar y preparar:
    Bash

    git clone <url-repo>
    cd fullstack
    npm install

    Iniciar servicios:

        Backend: npm run start:api (Puerto 3000)

        Frontend: npm run start:client (Puerto *)

API Endpoints
Método	Endpoint	Descripción
GET	/api/tasks	Obtiene todas las tareas
POST	/api/tasks	Crea una nueva tarea
PUT	/api/tasks/:id	Actualiza estado/contenido
DELETE	/api/tasks/:id	Elimina una tarea