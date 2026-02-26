---
inclusion: auto
description: Tech stack, build system, dependencies, common commands, and code style rules
---

# Tech Stack

## Language & Runtime

- TypeScript (strict mode enabled)
- Node.js 22+ required
- ESM modules (type: "module")

## Build System

- TypeScript compiler (tsc) for transpilation
- Bun for binary compilation
- pnpm for package management

## Key Dependencies

- commander: CLI framework
- @steipete/sweet-cookie: Browser cookie extraction (patched)
- json5: Config file parsing
- kleur: Terminal colors

## Testing & Quality

- vitest: Test runner with coverage (v8 provider)
- biome: Formatter and linter
- oxlint: Additional type-aware linting

## Common Commands

```bash
# Development
pnpm install              # Install dependencies
pnpm run dev <args>       # Run CLI in dev mode (tsx)
pnpm run build            # Build dist + binary
pnpm run build:dist       # Build dist only (TypeScript)
pnpm run build:binary     # Build standalone Bun binary

# Testing
pnpm test                 # Run all tests
pnpm test:watch           # Watch mode
pnpm test:live            # Run live API tests (requires auth)
pnpm test:live:all        # Run all live tests

# Code Quality
pnpm run lint             # Run biome + oxlint
pnpm run lint:fix         # Auto-fix issues
pnpm run format           # Format with biome

# Utilities
pnpm run graphql:update   # Update GraphQL query IDs
pnpm run bird <args>      # Run built CLI
```

## Code Style

- Single quotes for strings
- Semicolons required
- 2-space indentation
- 120 character line width
- Explicit .js extensions in imports (ESM requirement)
- No explicit any types
- No non-null assertions
- Prefer const over let
- Use template literals over concatenation

## Coverage Thresholds

- Statements: 90%
- Branches: 80%
- Functions: 90%
- Lines: 90%
