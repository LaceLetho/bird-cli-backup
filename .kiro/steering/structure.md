---
inclusion: auto
description: Project organization, architecture patterns, and naming conventions
---

# Project Structure

## Directory Layout

```
src/
├── cli/              # CLI infrastructure
│   ├── program.ts    # Commander program setup
│   ├── shared.ts     # Shared CLI context and utilities
│   └── pagination.ts # Pagination helpers
├── commands/         # Command implementations (one per file)
├── lib/              # Core library code
│   ├── twitter-client*.ts  # Client implementation (mixin pattern)
│   ├── query-ids.json      # GraphQL query ID mappings
│   ├── features.json       # GraphQL feature flags
│   └── *.ts                # Utilities and helpers
└── cli.ts            # CLI entry point
└── index.ts          # Library entry point

tests/                # Test files (mirrors src structure)
├── *.test.ts         # Unit tests
└── live/             # Live API integration tests

dist/                 # Build output (TypeScript compilation)
docs/                 # Documentation site
scripts/              # Build and utility scripts
```

## Architecture Patterns

### Mixin-Based Client

The TwitterClient uses a mixin pattern to compose functionality:

- `TwitterClientBase`: Core HTTP/auth logic
- `with*()` functions: Add specific capabilities (bookmarks, search, posting, etc.)
- Final `TwitterClient`: Composed class with all methods

Each feature area has its own file (e.g., `twitter-client-bookmarks.ts`, `twitter-client-search.ts`).

### Command Registration

Commands are registered in `src/cli/program.ts`:
- Each command has its own file in `src/commands/`
- Commands export a `register*Command()` function
- Registration functions attach commands to the Commander program

### Shared Context

`CliContext` (in `src/cli/shared.ts`) provides:
- Color/emoji output configuration
- Config file loading (JSON5)
- Credential resolution
- Output formatting helpers

## Key Files

- `src/lib/twitter-client.ts`: Main client export with all mixins
- `src/lib/twitter-client-types.ts`: Shared TypeScript types
- `src/lib/twitter-client-constants.ts`: API endpoints and constants
- `src/lib/query-ids.json`: GraphQL query ID mappings (rotates frequently)
- `src/lib/runtime-query-ids.ts`: Runtime query ID refresh logic
- `src/lib/cookies.ts`: Cookie extraction and credential resolution
- `src/lib/output.ts`: Output formatting utilities

## Naming Conventions

- Files: kebab-case (e.g., `twitter-client-bookmarks.ts`)
- Classes: PascalCase (e.g., `TwitterClient`)
- Functions/variables: camelCase (e.g., `getTweetDetail`)
- Types/interfaces: PascalCase (e.g., `TweetResult`)
- Constants: SCREAMING_SNAKE_CASE (e.g., `GRAPHQL_ENDPOINT`)

## Import Rules

- Always use `.js` extension in imports (ESM requirement)
- Prefer named exports over default exports
- Group imports: external deps, then internal modules
