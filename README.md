# Todo App - Golang + SQLite + Docker

Aplicación TODO con backend en Golang usando SQLite y frontend HTML servido con Nginx.

## Estructura del Proyecto

- **Backend**: Go con SQLite (CRUD completo)
- **Frontend**: HTML/CSS/JavaScript servido con Nginx
- **Base de datos**: SQLite (persistente en volumen Docker)

## Requisitos

- Docker
- Docker Compose

## Uso

### Ejecutar con Docker Compose

```bash
# Construir y levantar los servicios
docker-compose up --build

# O en modo detach (segundo plano)
docker-compose up -d --build
```

### Acceso

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8080 (directo) o http://localhost:3000/api (a través de nginx)

### API Endpoints

- `GET /api/todos` - Obtener todos los todos
- `POST /api/todos` - Crear un nuevo todo
- `PUT /api/todos/update?id={id}` - Actualizar un todo
- `DELETE /api/todos/delete?id={id}` - Eliminar un todo

### Detener los servicios

```bash
docker-compose down
```

### Ver logs

```bash
# Todos los servicios
docker-compose logs -f

# Solo backend
docker-compose logs -f backend

# Solo frontend
docker-compose logs -f frontend
```

## Desarrollo Local

### Backend

```bash
# Instalar dependencias
go mod download

# Ejecutar
go run main.go
```

### Base de Datos

La base de datos SQLite se guarda en `./data/todos.db` cuando se ejecuta con Docker.

## Notas

- El frontend se comunica con el backend a través de Nginx (proxy reverso)
- Los datos persisten en el volumen `./data` del host
- CORS está habilitado en el backend para permitir peticiones del frontend

