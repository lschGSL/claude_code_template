# CLAUDE.md — GSL Apps Project Template

## Project Identity

- **Project**: [PROJECT_NAME]
- **Stack**: Next.js 14 (App Router), TypeScript strict, Tailwind CSS, Supabase, Vercel
- **Repo**: github.com/lschGSL/[REPO_NAME]
- **Deploy**: [APP_NAME].vercel.app
- **Supabase project**: kwjgfljzdgpfyqknakmy.supabase.co

## GSL Group Context

GSL Group is a Luxembourg-based professional services group with three entities:
- **GSL Fiduciaire** — accounting/consulting (brand color: #5BAFD6)
- **GSL Révision** — audit (brand color: #CDD621)
- **GSL Group** — holding (brand color: #CC2936)

All GSL Apps share a unified SSO flow via apps.gsl.lu → `[app].vercel.app/auth/exchange`.

## Conventions

### Code Style
- TypeScript strict mode — no `any`, no implicit returns
- Functional components with hooks only
- Named exports for components, default exports for pages
- Path aliases: `@/` maps to `src/`
- File naming: `kebab-case` for files, `PascalCase` for components
- Use `server` components by default, `'use client'` only when needed

### Project Structure
```
src/
├── app/                    # Next.js App Router pages
│   ├── auth/
│   │   └── exchange/       # SSO callback route
│   ├── api/                # API routes
│   ├── layout.tsx          # Root layout
│   └── page.tsx            # Home page
├── components/
│   ├── ui/                 # Reusable UI primitives
│   └── [feature]/          # Feature-specific components
├── lib/
│   ├── supabase/
│   │   ├── client.ts       # Browser client
│   │   ├── server.ts       # Server client
│   │   └── middleware.ts   # Auth middleware
│   └── utils.ts            # Shared utilities
├── types/                  # TypeScript type definitions
└── styles/
    └── globals.css         # Tailwind + custom CSS
```

### Supabase SSO Pattern
```typescript
// src/app/auth/exchange/route.ts
import { createClient } from '@/lib/supabase/server'
import { NextResponse } from 'next/server'

export async function GET(request: Request) {
  const { searchParams } = new URL(request.url)
  const code = searchParams.get('code')
  if (code) {
    const supabase = await createClient()
    await supabase.auth.exchangeCodeForSession(code)
  }
  return NextResponse.redirect(new URL('/', request.url))
}
```

### Git & Commits
- Conventional commits: `feat:`, `fix:`, `docs:`, `refactor:`, `chore:`
- One logical change per commit
- Always update CHANGELOG.md for user-facing changes

### Documentation Files
| File | Purpose |
|------|---------|
| `CLAUDE.md` | This file — project context for Claude Code |
| `TODO.md` | Active task list, structured by priority |
| `CHANGELOG.md` | Version history, latest first |
| `DESIGN-SYSTEM.md` | Colors, typography, spacing, component patterns |
| `.env.local.example` | Required env vars (never commit actual values) |

### Testing
- Prefer integration tests over unit tests for pages/API routes
- Test files colocated: `component.test.tsx` next to `component.tsx`
- Run `npm run build` before committing to catch type errors

### Deployment
- Vercel auto-deploys from `main` branch
- Preview deployments on PRs
- Environment variables managed in Vercel dashboard

## File Edit Permissions

Claude Code may directly edit:
- `CLAUDE.md`, `TODO.md`, `CHANGELOG.md`, `DESIGN-SYSTEM.md`, `.env.local.example`

All other files: ask Luc first or follow explicit instructions.

## Skills

See `/skills/` directory for reusable coding patterns and instructions.
