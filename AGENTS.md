# AGENTS.md

## Project Overview

OpenCode plugin that sends Discord webhook notifications on session
completion and permission requests.

## Commands

### Build
```
npm run build
```
Bundles `src/index.ts` to `dist/index.js` (ESM) using tsup.

### Typecheck
```
npx tsc
```
TypeScript strict mode, `noEmit: true` — type-checking only.

## Code Conventions

- Single source file: `src/index.ts`
- ESM modules (`"type": "module"` in package.json)
- Zero runtime dependencies — uses only Node.js built-ins
- Peer dependency: `@opencode-ai/plugin`
- Plugin entry point exports `DiscordNotificationPlugin` (async plugin factory)
- `verbatimModuleSyntax: true` — always use `import type` for type-only imports
