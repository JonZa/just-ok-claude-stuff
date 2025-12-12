---
name: typescript-conventions
description: Apply when writing TypeScript outside Vue components — services, utilities, types, API layer.
---

# TypeScript Conventions

## Strictness

Strict mode enabled. No `any` without explicit justification.

## Interface vs Type

```typescript
// Interface: object shapes (props, state, API responses)
interface SessionState {
  user: User | null
  isLoading: boolean
}

// Type: unions, aliases, utility types
type InputType = 'text' | 'email' | 'number' | 'date'
type BadgeColor = 'yellow' | 'gray' | 'blue' | 'red'
```

## Type Location

- **ui-vue:** Co-located with components (`export interface BaseButtonProps`)
- **Apps:** Separate `/types/` directory for shared types, inline for local

## Runtime Validation

Zod for schemas that need runtime validation:

```typescript
const queryParamsSchema = z.object({
  sort_by: z.enum(VALID_SORT_BY_OPTIONS).optional(),
  filter: z.enum(VALID_FILTER_OPTIONS).optional(),
})
```

## Generics

Use for composables and utilities that operate on variable types:

```typescript
export function useModalSubmission<T extends Record<string, unknown>, R = unknown>(
  options: UseModalSubmissionOptions<T, R>,
  modalState: Ref<boolean>,
)
```

## Prefer

- `satisfies` for type narrowing with inference
- Explicit return types on exported functions
- Discriminated unions over type assertions
