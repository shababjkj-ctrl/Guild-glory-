# Guild Glory — Render-ready

This project uses `aiohttp`, not Flask/FastAPI. The public web application is exposed
as the module-level `main:app` object for Gunicorn. `dashboard_server.py` is retained as a
legacy/alternate aiohttp dashboard module and now points to the same HTML file.

## Render

Build:
`pip install -r requirements.txt`

Start:
`gunicorn main:app --bind 0.0.0.0:$PORT --worker-class aiohttp.GunicornWebWorker --workers 1 --timeout 0`

The app reads Render's `PORT` environment variable and binds to `0.0.0.0`.

## Dashboard

`/` and `/index.html` serve `PRNCODEX/index.html`.

## Runtime data

`accounts.json` and `token_cache.json` are intentionally empty in this deploy package.
The original credential-bearing files are retained only as `.example` files and should
not be committed with real credentials.

## Environment variables

- `PORT` — supplied automatically by Render.
- `HOST` — optional; defaults to `0.0.0.0`.
- `PYTHON_VERSION` — set to `3.12.10` in `render.yaml`.

Game/account data is supplied through the dashboard/API at runtime.
