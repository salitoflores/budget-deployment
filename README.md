# 📦 budget-deployment

`budget-deployment` es un entorno de despliegue basado en Docker Compose para una aplicación de gestión presupuestaria. Este proyecto simplifica el proceso de configuración, ejecución y escalado del sistema completo con un solo comando.

---

## 🧩 Arquitectura del Proyecto

Este entorno incluye múltiples servicios que pueden variar dependiendo de tu stack. Por defecto, puede incluir:

- **backend**: API REST construida con Spring Boot.
- **frontend**: Aplicación React.
- **database**: PostgreSQL / Redis.
- **nginx**: Servidor proxy inverso (opcional).
- **adminer / pgadmin**: Interfaz de administración para la base de datos (opcional).

---

## 🚀 Requisitos Previos

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/)

---

## 📖 Configuraciones previas
Antes de ejecutar el docker hay que tener previamente configurado la base de datos se puede instalar mediante instalación local o mediante docker, para esto se debe tener en cuenta lo siguiente:
- **Base de datos**: Asegúrate de tener una base de datos PostgreSQL configurada y accesible. Puedes usar un contenedor Docker para esto, puedes instalarlo con el siguiente comando:

  ```bash
  docker run -d --name postgres_local --restart always -e POSTGRES_USER=admin -e POSTGRES_PASSWORD=secret -p 5432:5432 -v pgdata:/var/lib/postgresql/data postgres:15
  ```
- **Creación bases de datos**: Crea las bases de datos necesarias para tu aplicación. Por ejemplo, si tu aplicación necesita una base de datos llamada `budget_db`, puedes crearla con el siguiente comando:

  ```sql
  CREATE DATABASE budget;
  CREATE DATABASE budget_administration;
  CREATE DATABASE budget_security;
  ```

---

## 🔧 Instalación

1. Clona este repositorio:

   ```bash
   git clone https://github.com/salitoflores/budget-deployment.git
   cd budget-deployment
   ```

2. Crea un archivo `.env` (si es necesario):

   ```bash
   cp .env.example .env
   ```

3. Construye y levanta los contenedores:

   ```bash
   docker-compose up --build
   ```

---

## 📂 Estructura del Proyecto

```text
budget-deployment/
├── docker-compose.yml
├── .env
└── README.md
```

---

## 📌 Comandos Útiles

- Levantar todos los servicios en segundo plano:

  ```bash
  docker-compose up -d
  ```

- Detener todos los servicios:

  ```bash
  docker-compose down
  ```

- Ver logs:

  ```bash
  docker-compose logs -f
  ```

- Reconstruir sin usar cache:

  ```bash
  docker-compose build --no-cache
  ```

---

## 🛠 Variables de Entorno

El archivo `.env` permite configurar variables como:

```env
JWT_SECRET_KEY=key...
SPRING_DATASOURCE_URL=secret
SPRING_DATASOURCE_URL_BUDGET=budget_db
SUFFIX=_environment
```

---

## 🐳 Despliegue

Puedes desplegar este entorno en cualquier servidor compatible con Docker. También puedes adaptarlo para plataformas como:

- Docker Swarm
- Kubernetes
- DigitalOcean App Platform
- Render

---

## 📄 Licencia

Este proyecto está licenciado bajo la [MIT License](LICENSE).

---

## 📬 Contacto

Si tienes preguntas o sugerencias:

- Email: salitoflores@gmail.com
- GitHub: [@salitoflores](https://github.com/salitoflores)
