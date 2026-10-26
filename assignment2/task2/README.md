# Task 2: Docker Compose (Flask + Redis)

Based on the Docker Compose Quickstart (https://docs.docker.com/compose/gettingstarted).

## Files
- `app.py`: Flask app with a hit counter stored in Redis
- `requirements.txt`: flask, redis
- `.env`: port and Redis settings
- `.dockerignore`: files excluded from the image build
- `Dockerfile`: only 4 lines (FROM, ADD, WORKDIR, RUN)
- `compose.yml`: services, network and volume

## What changed from the tutorial
- The Dockerfile was reduced to 4 lines. The start command (`flask run --debug`) and the environment variables (`FLASK_APP`, `FLASK_RUN_HOST`) moved into `compose.yml`.
- Added a network `app_net` so web and redis can communicate by service name.
- Added a volume `code_vol` mounted at `/code` so the web service stores the code.

## Commands
- `docker compose up -d --build`
- `docker compose ps`
- `docker network ls`
- `docker volume ls`
- `docker compose down`

## Result
Opening http://localhost:8000 shows "Hello from Docker! I have been seen N time(s)." and N increases on every refresh, which proves web can reach redis over the network.
