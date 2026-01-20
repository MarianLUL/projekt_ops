# Weather Docker Compose Demo

Krátký demo projekt: jednoduché backend API (FastAPI) a frontend (statický HTML), vše spustitelné pomocí `docker-compose`.

Rychlý start:

1) Zkopírujte `.env.example` do `.env` a vložte svůj OpenWeatherMap API klíč.

```powershell
copy .env.example .env
# upravte .env a zadejte OPENWEATHER_API_KEY
```

2) Spuštění (Docker) - Windows 11 doporučeno

Pokud používáte Docker Desktop na Windows 11, ujistěte se, že je Docker Desktop spuštěný (WSL2 doporučeno).

```powershell
docker-compose up --build
```

Frontend bude dostupný na http://localhost:8080
API bude dostupné na http://localhost:8000

Spuštění bez Dockeru (Windows)

```powershell
# Spustit backend lokálně
.\run-backend.ps1

# V dalším okně terminálu spustit frontend
.\run-frontend.ps1
```

Poznámky:
- Pokud frontend poběží v Docker kontejneru, pro připojení k backendu v hostu používáme `host.docker.internal`.
- `frontend/index.html` zkusí postupně: relativní `/weather/...`, `host.docker.internal` a `localhost`, takže by měl fungovat lokálně i v Docker Compose na Windows.
