# Proyecto n8n con Base de Datos Vectorial y OpenAI

Este proyecto implementa un entorno **n8n** en Docker para automatizar
flujos de trabajo de IA con **OpenAI** y **Supabase** como base de datos
vectorial.

Incluye: - Contenedor n8n con PostgreSQL como base de datos. - Workflows
para **traer datos desde una BD vectorial** y **agregar embeddings a una
BD vectorial**.

## 1️⃣ Requisitos previos

-   Docker y Docker Compose instalados.
-   Cuenta en [OpenAI](https://platform.openai.com/) con API Key.
-   Base de datos en [Supabase](https://supabase.com/) para almacenar
    los embeddings.

## 2️⃣ Estructura de archivos

    .
    ├─ docker-compose.yml
    ├─ Traer Datos desde BD Vectorial.json
    └─ Agregar Embeddings a una BD vectorial.json

### Archivos principales

-   **docker-compose.yml**: Define los contenedores `n8n` y `postgres`.
-   **Traer Datos desde BD Vectorial.json**: Workflow de n8n para
    consultar embeddings de Supabase y responder a consultas en lenguaje
    natural.
-   **Agregar Embeddings a una BD vectorial.json**: Workflow de n8n para
    insertar datos y generar embeddings en Supabase.

## 3️⃣ Puesta en marcha

1.  **Clonar el repositorio o copiar los archivos en un directorio
    local.**
2.  Crear un archivo `.env` (opcional) si quieres manejar las variables
    de entorno de forma separada.
3.  Levantar los servicios:

``` bash
docker compose up -d
```

Esto crea: - Un contenedor `n8n` accesible en <http://localhost:5678>. -
Un contenedor `postgres` como base de datos de n8n.

## 4️⃣ Configuración de n8n

1.  Accede a la interfaz web de n8n.
2.  Importa los workflows:
    -   **Traer Datos desde BD Vectorial.json**
    -   **Agregar Embeddings a una BD vectorial.json**
3.  Configura las credenciales:
    -   **OpenAI API Key** en las credenciales `OpenAi account`.
    -   **Supabase URL y Key** en las credenciales `Supabase account`.

## 5️⃣ Ejecución de los workflows

-   **Agregar Embeddings a una BD vectorial**: Ejecuta manualmente este
    flujo para cargar nuevos documentos y generar embeddings en
    Supabase.
-   **Traer Datos desde BD Vectorial**: Se activa al recibir un mensaje
    de chat y consulta la base vectorial para responder.

## 6️⃣ Personalización

-   Cambia la clave `N8N_ENCRYPTION_KEY` en `docker-compose.yml` para
    mayor seguridad.
-   Ajusta los parámetros de conexión de la base de datos en las
    variables `DB_*` si deseas usar otra base de datos.

## 7️⃣ Comandos útiles

-   Detener los servicios:

``` bash
docker compose down
```

-   Ver logs en tiempo real:

``` bash
docker compose logs -f
```

------------------------------------------------------------------------

Con esta configuración, tendrás un entorno automatizado para **almacenar
documentos en una base vectorial** y **consultarlos mediante IA de
OpenAI** dentro de n8n.
