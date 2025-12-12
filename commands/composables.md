Identify opportunities to extract logic into Vue composables.

**$ARGUMENTS:** Optional file path or directory to scope the audit

Apply **vue-conventions** skill for composable patterns.

Look for:

- Repeated patterns across components
- Stateful logic (reactive state, refs, computed)
- Side effects (lifecycle hooks, watchers, event listeners)
- Data fetching or API patterns
- Complex reusable logic

For each opportunity:

- Show current code location
- Propose `useName` composable implementation
- Show refactored component usage

Prioritize extractions that improve reusability or significantly simplify components.
