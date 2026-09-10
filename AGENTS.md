# Base44 Dev Environment

## Project
Frontend-only Vite + React + TypeScript app (Lovable scaffold). No backend, no database, no external API credentials required.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Vite dev server runs on port 8080 inside the container, mapped to host port 3000.
- Dependencies are installed on each container start via `npm install` (node_modules is an anonymous volume to avoid host conflicts).

## Notes
- Vite config sets `server.port: 8080` and `server.host: "::"`. The compose command overrides host to `0.0.0.0`.
- `__VITE_ADDITIONAL_SERVER_ALLOWED_HOSTS` is passed through from the platform environment so the preview proxy host is allowed.
- Uses `@vitejs/plugin-react-swc` for fast refresh; edits to source files hot-reload in the preview.
- shadcn/ui components live in `src/components/ui/`. Tailwind CSS is configured via `tailwind.config.ts` + `postcss.config.js`.
