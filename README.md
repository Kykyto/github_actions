Docker Compose - 3-Tier App

This project uses Docker Compose to run three services:

- **PostgreSQL** database  
- **Spring Boot** backend API (`simple-api`)  
- **Apache HTTP Server** (`httpd`)

---

## Services

### database
- Builds from the `database/` folder
- Uses `POSTGRES_PASSWORD=pwd`
- Stores data in a volume (`db-volume`)
- Part of the shared network `my-network`

### simple-api
- Builds from the `simple-api/` folder
- Connects to the `database` container using `DATABASE_HOST=database`
- Uses the same password (`DATABASE_PASSWORD=pwd`)
- Part of the same network

### httpd
- Builds from the `http-server/` folder
- Exposes port `80` to the host (open in browser: http://localhost)
- Can be configured as a reverse proxy to the backend

---

## Networks

- All services are in the same custom Docker network called `my-network`

---

## Volumes

- `db-volume`: stores PostgreSQL data so it persists even if the container is deleted

---

# After Launching
Visit the front-end: http://localhost:3000

Visit the HTTP server or backend (if proxied): http://localhost
