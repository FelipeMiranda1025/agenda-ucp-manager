# 🚀 Agenda Docente UCP - Orquestador de Servicios

Este repositorio es el punto central del proyecto **Agenda Docente**. Utiliza **Git Submodules** para gestionar los repositorios independientes de Backend, Frontend y Base de Datos, y **Docker Compose** para orquestar el despliegue local.

---

## 🛠️ Requisitos Previos

Antes de comenzar, asegúrate de tener instalado:
* [Docker Desktop](https://www.docker.com/products/docker-desktop/)
* [Git](https://git-scm.com/)

---

## 📥 1. Clonación del Proyecto

Como este proyecto utiliza submódulos, es **CRUCIAL** clonarlo usando el parámetro `--recursive`. De lo contrario, las carpetas de los módulos aparecerán vacías.

```powershell
git clone --recursive [https://github.com/FelipeMiranda1025/agenda-ucp-manager.git](https://github.com/FelipeMiranda1025/agenda-ucp-manager.git)
cd agenda-ucp-manager
Nota: Si ya clonaste el proyecto sin el comando anterior, ejecuta:
git submodule update --init --recursive

⚙️ 2. Configuración de Variables de Entorno (.env)
Por seguridad, los archivos .env no se suben al repositorio. Debes crearlos manualmente siguiendo estos pasos:

Backend
Entra a agenda-ucp-backend/.

Busca el archivo .env.example.

Crea una copia y renómbrala a .env.

Verifica que las credenciales de la base de datos coincidan con las del docker-compose.yml.

Frontend
Entra a agenda-ucp-frontend/.

Repite el proceso (copiar .env.example a .env).

🏗️ 3. Despliegue con Docker
Desde la raíz del proyecto (agenda-ucp-manager), ejecuta el siguiente comando para construir y levantar todos los servicios (Base de Datos, Backend y Frontend):

PowerShell
docker compose up -d --build
Esto hará lo siguiente:

Levantará PostgreSQL en el puerto 5432.

Levantará el Backend en el puerto 3000.

Levantará el Frontend en el puerto 80.

🔑 4. Inyección del Usuario Inicial (Soporte)
Como la base de datos está vacía inicialmente, debes crear el usuario de soporte para poder ingresar al sistema:

Identifica el nombre del contenedor del backend (usualmente agenda-ucp-backend-1).

Ejecuta el comando de inyección:

PowerShell
docker exec -it agenda-ucp-backend-1 npm run seed:support
(O el comando específico que definimos para crear el usuario 12345).

🔄 5. Flujo de Trabajo con Submódulos
Para mantener el proyecto actualizado:

Para obtener cambios del equipo:

PowerShell
git pull origin main
git submodule update --remote --merge
Para subir cambios:
Los cambios de código se suben dentro de cada carpeta (backend o frontend). Luego, en la raíz, se hace un commit para actualizar la referencia del submódulo.

🗂️ Estructura del Proyecto
/agenda-ucp-backend: Lógica de negocio y API (NestJS/Node).

/agenda-ucp-frontend: Interfaz de usuario (React/Vite).

/agenda-ucp-db: Configuraciones específicas de la base de datos.

docker-compose.yml: Archivo de orquestación de contenedores.


---

### Por qué este README es efectivo:
1.  **Advertencia del `--recursive`:** Es el error #1 al trabajar con submódulos. Ponerlo al principio evita frustraciones.
2.  **Sección de `.env`:** Explica claramente que no existen por defecto y hay que crearlos, lo cual evita que el `docker-compose` falle por falta de variables.
3.  **Comandos directos:** Tu compañero solo tiene que copiar y pegar.
4.  **Explicación de Git:** Ayuda a entender que hay "dos niveles" de Git (la raíz y los módulos).



**¿Te gustaría añadir alguna sección de contacto o requisitos específicos de hardware antes de guardarlo?**