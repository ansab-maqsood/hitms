# HITMS — Higher Education Information & Teaching Management System

HITMS is being built as a real university-grade academic management platform.

## Current foundation

- React + TypeScript + Vite
- Supabase/PostgreSQL integration point
- Cloudflare Workers deployment configuration
- Responsive admin dashboard
- Student registry foundation
- Modules for faculty, courses, sections, assessments, results, attendance, reports, audit log and settings
- Initial PostgreSQL schema with role model and Row Level Security foundation

## Architecture

Browser → Cloudflare Workers → React application  
                         ↘ Supabase Auth / PostgreSQL / Storage

The browser must never contain a Supabase service-role key. Only the publishable key belongs in the frontend environment.

## Local setup

1. Install Node.js LTS.
2. Open this project folder in a terminal.
3. Run:

```bash
npm install
npm run dev
```

4. Open the local URL printed by Vite.

## Supabase setup

1. Create a Supabase project.
2. Open SQL Editor.
3. Run `supabase/schema.sql`.
4. Copy `.env.example` to `.env.local`.
5. Put the Supabase Project URL and Publishable Key in `.env.local`.

Example:

```env
VITE_SUPABASE_URL=https://YOUR-PROJECT.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=YOUR-PUBLISHABLE-KEY
```

## Cloudflare

The repository already contains `wrangler.toml` for the HITMS SPA.

Build:

```bash
npm run build
```

Deploy after authentication to Cloudflare:

```bash
npm run deploy
```

For the GitHub/Cloudflare workflow, commit and push changes to the `hitms` repository and use Cloudflare's connected deployment.

## Development roadmap

### Phase 1 — Foundation
- UI shell
- authentication
- roles
- departments/programs/courses
- students/faculty
- audit logging

### Phase 2 — Academic operations
- sections and enrollments
- attendance
- assignments/case studies
- midterm/final marks
- result calculations
- Excel/PDF exports

### Phase 3 — Online assessment
- question bank
- randomized tests
- timer
- auto-save
- auto-submit
- objective auto-marking
- result release controls

### Phase 4 — Production hardening
- granular RLS
- rate limiting
- backup/recovery procedures
- security headers
- secrets management
- monitoring
- load/concurrency testing
- independent penetration testing before production use

## Important

The dashboard currently contains clearly marked demo data so the interface can be reviewed before connecting a real university database. Demo data must be replaced by database-backed records before production use.
