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

Windows virtual environment (venv)

If you prefer running the backend in a local Python virtual environment on Windows, here are the exact steps I used:

1. Change to the backend folder:

```powershell
Set-Location backend
```

2. Create the virtual environment with the `py` launcher:

```powershell
py -3 -m venv venv
```

3. Activate the venv (PowerShell):

```powershell
.\venv\Scripts\Activate.ps1
```

If you use Command Prompt (cmd.exe) instead, activate with:

```powershell
.\venv\Scripts\activate.bat
```

4. Install dependencies and run the backend:

```powershell
pip install -r requirements.txt
py -3 -m uvicorn main:app --reload --port 8000
```

After that open http://localhost:8000 in your browser to access the UI and API.

Poznámky:
- Pokud frontend poběží v Docker kontejneru, pro připojení k backendu v hostu používáme `host.docker.internal`.
- `frontend/index.html` zkusí postupně: relativní `/weather/...`, `host.docker.internal` a `localhost`, takže by měl fungovat lokálně i v Docker Compose na Windows.
