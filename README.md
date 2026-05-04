🚀 Agenda Docente UCP - Guía de Inicio Rápido
Este proyecto es un ecosistema de microservicios que utiliza React (Frontend), Node.js (Backend) y PostgreSQL (Base de datos), todo orquestado con Docker.

📋 Requisitos Previos
Antes de empezar, asegúrate de tener instalado:

Docker Desktop (Asegúrate de que esté abierto).

Git.

🛠️ Configuración Inicial
1. Estructura de carpetas
Asegúrate de tener los repositorios organizados de la siguiente manera:

Plaintext
/agenda-docente-root
├── docker-compose.yml
├── agenda-ucp-backend/
├── ucp-agenda-frontend/
└── agenda-ucp-db/
2. Variables de Entorno
Ve a la carpeta agenda-ucp-backend/.

Crea un archivo llamado .env.

Copia y pega el contenido de .env.example (o pide las credenciales al administrador).

Nota: Asegúrate de que DB_HOST=db para que Docker lo reconozca.

🚀 Ejecución del Proyecto
Abre una terminal en la carpeta raíz y ejecuta el siguiente comando:

PowerShell
docker compose up -d --build
Este comando descargará las imágenes, construirá los contenedores y los pondrá a correr en segundo plano.

🔑 Acceso y Primeros Pasos
1. Inyectar Usuario Administrador
Como la base de datos inicia vacía, debes ejecutar este comando una sola vez en tu terminal para crear el usuario de soporte:

PowerShell
docker exec -i agenda-ucp-db psql -U postgres -d agendadocentedb -c "INSERT INTO roles (id, nombre) VALUES (5, 'Soporte') ON CONFLICT DO NOTHING; INSERT INTO users (cc, nombre, password, id_rol) VALUES ('12345', 'Admin Soporte', '9709c065f4d1e2e176211832d2011116c4f6918805f42c23f20f324e93019d67', 5) ON CONFLICT DO NOTHING;"
2. Entrar al Sistema
URL: http://localhost

Cédula: 12345

Contraseña: 1234Ucp*

🔄 Flujo de Trabajo (Día a Día)
Si haces cambios en el código o bajas actualizaciones de Git, usa:

Actualizar cambios: git pull y luego docker compose up -d --build.

Ver logs (errores): docker compose logs -f backend.

Apagar el sistema: docker compose down.

⚠️ Solución de Problemas Comunes
Error de CORS: Si el sistema carga pero el login falla, presiona Ctrl + F5 en el navegador para limpiar la caché.

Puerto ocupado: Asegúrate de que no tengas otros servicios corriendo en los puertos 80, 4000 o 5432.

Desarrollado para la UCP 🎓