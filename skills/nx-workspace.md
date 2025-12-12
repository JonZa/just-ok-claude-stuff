---
name: nx-workspace
description: Apply when working with project structure, imports, generators, or build commands. Ensures correct paths, naming, and Nx patterns.
---

# Nx Workspace Conventions

## Structure

```
skypaygroup/
├── packages/           # Shared libraries (@plt/types, @plt/ui-vue)
├── platform/           # Infrastructure services
├── plt/                # PLT business domain
│   └── _packages/      # PLT-specific shared packages
├── slice-engine/       # Fintech engine domain
│   └── _packages/      # Domain-specific packages
├── slice-pay/          # B2B payments domain
└── tools/              # Generators, executors
```

## Project Naming

Pattern: `{scope}#{type}#{name}` or `{scope}#{name}`

```
package#types                              # packages/types
packages#ui-vue                            # packages/ui-vue
slice-engine#repayments                    # slice-engine/repayments
slice-engine#repayments-admin-console-vue-app  # nested vue app
plt#package#domain-events                  # plt/_packages/domain-events
tool#generators                            # tools/generators
```

## Tags

| Tag               | Meaning                                        |
| ----------------- | ---------------------------------------------- |
| `deployable`      | Has Pulumi infra                               |
| `publishable`     | Published to npm                               |
| `type:app`        | Frontend application                           |
| `type:ui-library` | UI component library                           |
| `scope:{domain}`  | Domain boundary (repayments, booking-creation) |

## Import Paths

```typescript
// Shared packages
import { BaseButton } from '@plt/ui-vue'
import { SomeType } from '@plt/types'

// Never import directly from node_modules for:
// - zod → use @plt/types
// - xml2js → use @plt/xml
// - @pulumi/* → use @plt/pulumi
```

## Common Commands

```bash
# Run across workspace
pnpm compile          # nx run-many -t compile
pnpm lint             # nx run-many -t lint
pnpm test             # nx run-many -t test

# Run affected only
nx affected -t compile
nx affected -t test

# Run specific project
nx run slice-engine#repayments:compile
nx run packages#ui-vue:storybook:dev

# Deploy
nx run slice-engine#repayments:pulumi -- au.staging preview
nx run slice-engine#repayments:pulumi -- au.staging up
```

## Creating New Projects

```bash
pnpm new-service      # TypeScript service (prompts for company/team/name)
pnpm new-service-go   # Go service
pnpm new-package      # Shared package
```

## Standard Targets

| Target      | Purpose                   | Cached |
| ----------- | ------------------------- | ------ |
| `compile`   | TypeScript compilation    | ✓      |
| `lint`      | ESLint                    | ✓      |
| `test`      | Jest/Vitest               | ✓      |
| `codecheck` | Full code validation      | ✓      |
| `pulumi`    | Infrastructure deployment | ✗      |

## Vue Apps Location

Frontend apps nest inside services:

```
slice-engine/repayments/src/service/admin-console/vue-app/
```

## Workspace Dependencies

```json
// package.json
{
  "dependencies": {
    "@plt/types": "workspace:*"
  }
}
```
