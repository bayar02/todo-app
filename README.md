# To-Do App (DevOps Practice Project)

Simple full-stack app: HTML/JS frontend, Node/Express backend, PostgreSQL database.
Built as a step-by-step DevOps learning project — Docker now, Jenkins/Ansible/AWS/Grafana next.

## Run locally

Requirements: Docker + Docker Compose installed.

```bash
docker-compose up --build
```

Then open: http://localhost

- Frontend: http://localhost (served by Nginx)
- Backend API: http://localhost/api/todos (proxied through Nginx to the backend container)
- Database: Postgres running internally, not exposed to host

To stop:
```bash
docker-compose down
```

To stop AND wipe the database:
```bash
docker-compose down -v
```

## Project structure

```
todo-app/
├── docker-compose.yml     # orchestrates all 3 services
├── backend/
│   ├── Dockerfile
│   ├── package.json
│   └── src/server.js      # Express REST API
└── frontend/
    ├── Dockerfile
    ├── nginx.conf          # proxies /api/* to backend container
    └── index.html          # plain JS frontend, no build step
```

## API endpoints

- `GET /api/health` — health check
- `GET /api/todos` — list all todos
- `POST /api/todos` — create a todo `{ "title": "..." }`
- `PATCH /api/todos/:id` — toggle done status
- `DELETE /api/todos/:id` — delete a todo
