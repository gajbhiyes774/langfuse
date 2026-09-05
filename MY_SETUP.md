# Langfuse — My Setup & Integration

## Original Project

**Original Repository:** https://github.com/langfuse/langfuse

**Original Authors / Organization:** Langfuse

**License:** MIT (mixed — portions under ClickHouse + enterprise; see `LICENSE`)

**My Fork:** https://github.com/gajbhiyes774/langfuse

> **Open Source Project — Setup & Integration** — Original code, license, attribution preserved.

---

## What This Project Does

Open source AI engineering platform: LLM evals, traces, prompt management, observability for LLM apps (alternative to LangSmith).

---

## Technologies

TypeScript • Next.js • Postgres • ClickHouse • Redis • Docker Compose • pnpm

---

## How I Configured It

### 1. Fork & Clone
```bash
gh repo fork langfuse/langfuse --clone=false
# fork: https://github.com/gajbhiyes774/langfuse
git clone --depth 1 https://github.com/langfuse/langfuse.git
git remote add fork https://github.com/gajbhiyes774/langfuse.git
```

### 2. Prerequisites Checked
- `docker-compose.yml` (services: clickhouse, postgres, redis, langfuse)
- `docker --version 29.6.1` ✅
- `docker compose version v5.3.0` ✅
- `docker compose config` → parses correctly (services, ClickHouse image `clickhouse/clickhouse-server:25.12`)
- But `docker ps` → `dockerDesktopLinuxEngine: The system cannot find the file specified`
- `sc query com.docker.service` → STOPPED (same as qdrant)

### 3. Attempted Run
```bash
docker compose up -d
# → failed to connect to docker API at npipe:////./pipe/dockerDesktopLinuxEngine
```

Per `README.md` / `docker-compose.yml` and https://langfuse.com/docs/deployment/self-host:
```bash
docker compose up -d  # + requires .env with NEXTAUTH_SECRET, DATABASE_URL, etc.
```

---

## Problems Encountered & Solutions

| Problem | Solution |
|---------|----------|
| `failed to connect to docker API at npipe:////./pipe/dockerDesktopLinuxEngine` | **Start Docker Desktop** on Windows (Start Menu → Docker Desktop) then `docker compose up -d`. Linux: `sudo systemctl start docker`. |
| Needs Postgres + ClickHouse + Redis | Already in `docker-compose.yml`; Docker handles it when daemon runs |

**Changes made:** None — only this `MY_SETUP.md`.

---

## My Contribution

- [x] Forked via GitHub fork (preserved attribution & MIT)
- [x] Cloned original (depth 1, 5708 files)
- [x] Verified `docker compose config` parses
- [x] Diagnosed Docker daemon STOPPED (same host issue as qdrant)
- [x] Documented fix

---

## Test Report

| Test | Result |
|------|--------|
| `docker --version` | ✅ 29.6.1 |
| `docker compose config` | ✅ parses |
| `docker compose up -d` | ❌ Blocked — daemon STOPPED |

After starting Docker Desktop:
```bash
docker compose up -d
curl http://localhost:3000  # Langfuse UI
```

---

## License Preservation

`LICENSE` retained (MIT + ClickHouse portions).

---

## Portfolio Card

**Langfuse — Open Source Project — Setup & Integration**

- Original: https://github.com/langfuse/langfuse
- My Fork: https://github.com/gajbhiyes774/langfuse
- Tech: Next.js • Docker • ClickHouse
- My Work: Fork, clone, diagnosed Docker daemon stopped
- License: MIT (mixed)

