<p align="center">
  <img src="https://cdn-icons-png.flaticon.com/512/8569/8569864.png" width="120" alt="eslightning logo" />
</p>

<h1 align="center">ESLightning</h1>

<p align="center">
  Opinionated ESLint configurations for TypeScript projects.
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/eslightning">
    <img src="https://img.shields.io/npm/v/eslightning.svg" alt="npm version" />
  </a>
  <a href="https://www.npmjs.com/package/eslightning">
    <img src="https://img.shields.io/npm/dm/eslightning.svg" alt="npm downloads" />
  </a>
  <a href="https://github.com/manoel-lopes/eslightning/blob/main/LICENSE">
    <img src="https://img.shields.io/npm/l/eslightning.svg" alt="license" />
  </a>
</p>

## What's included?

- ESLint recommended rules
- TypeScript ESLint strict configuration
- Neostandard (modern JavaScript style guide)
- Vitest globals support
- Import sorting and validation
- Unused imports removal
- Prettier-compatible formatting

## Setup

### Node.js

Install the dependencies:

```bash
pnpm add -D eslightning eslint typescript
```

Create an `eslint.config.mjs` file:

```js
import node from 'eslightning/node'

export default [
  ...node,
]
```

### With custom ignores

```js
import node from 'eslightning/node'

export default [
  {
    ignores: ['dist/**', 'node_modules/**'],
  },
  ...node,
]
```

### Overriding rules

```js
import node from 'eslightning/node'

export default [
  ...node,
  {
    rules: {
      '@typescript-eslint/no-explicit-any': 'off',
    },
  },
]
```

## Rules

### TypeScript Strict

| Rule | Level | Description |
|------|-------|-------------|
| `no-explicit-any` | error | Disallow `any` type |
| `consistent-type-assertions` | error | Disallow `as` keyword (no type assertions) |
| `no-unnecessary-type-assertion` | error | Disallow unnecessary type assertions |
| `no-unused-vars` | warn | Warn on unused variables (ignores `_` prefix) |

### Code Style

| Rule | Level | Description |
|------|-------|-------------|
| `max-len` | warn | Maximum 120 characters per line |
| `no-console` | error | Disallow console (except `console.error`) |
| `no-var` | error | Require `let` or `const` instead of `var` |
| `no-multiple-empty-lines` | warn | Maximum 1 empty line |

### Import Organization

Imports are automatically sorted in the following order:

1. Node.js built-ins (`node:`)
2. External packages
3. `@nestjs/*` packages
4. `@prisma/*` packages
5. Project aliases (`@/core`, `@/domain`, `@/infra`, etc.)
6. Relative imports

Additional import rules:
- Unused imports are automatically removed
- Import paths are validated
- Exports are sorted

### Class Members

| Context | Blank Line |
|---------|------------|
| Between fields | Never |
| Between methods | Always |
| Between field and method | Always |

### Testing (Vitest)

Vitest globals are available without imports:
- `describe`, `it`, `test`
- `expect`, `vi`
- `beforeAll`, `afterAll`, `beforeEach`, `afterEach`

Test files (`*.test.ts`, `*.spec.ts`) have relaxed padding rules.

## Peer Dependencies

| Package | Version |
|---------|---------|
| `eslint` | >= 9.0.0 |
| `typescript` | >= 5.0.0 |

## License

MIT
