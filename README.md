# Open Scripture Explorer

Open Scripture Explorer is a Hebrew-first Scripture study PWA.

Phase 1 is intentionally narrow:

- Mobile-first Search and Bible tabs
- Hebrew-first Tanakh reader
- JPS 1917 English translation under the Hebrew text
- AI Scripture search that returns references only
- Backend-verified Scripture quotations from the local database
- Local-only search history

## Current Checkpoint

This repository is scaffolded with:

- Next.js app router
- JavaScript
- Tailwind CSS
- Prisma schema for `books`, `chapters`, and `verses`
- Full local Tanakh reader data
- Basic reference parser
- Initial unit tests and Playwright smoke test scaffold

The AI search service is not implemented yet.

## Scripture Data

The reader uses generated local data at `src/data/tanakh.json`.

Current import:

- Hebrew: `HBOMAS`, Hebrew Masoretic OT from HelloAO/eBible
- English: `eng_jps`, JPS TaNaKH 1917 from HelloAO/eBible
- Scope: 39 Tanakh books, 929 chapters, 23,213 OSHB/MT-numbered verses

Regenerate the local data with:

```bash
npm run import:tanakh
```

Source metadata is stored in `src/data/sources.json`.

## Local Setup

```bash
npm install
cp .env.example .env
npm run dev
```

Open http://localhost:3000.

## Verification

```bash
npm run lint
npm test
npm run prisma:validate
npm run build
```

The browser smoke test can be run after Playwright browsers are installed:

```bash
npx playwright install
npx playwright test
```

## Required Environment

```bash
DATABASE_URL=
OPENAI_API_KEY=
DEFAULT_AI_PROVIDER=openai
APP_ENV=development
```

## Phase 1 Guardrails

Do not add accounts, chat threads, AI commentary, multiple translations, Strong's,
morphology, transliteration, notes, highlights, bookmarks, or social features.
