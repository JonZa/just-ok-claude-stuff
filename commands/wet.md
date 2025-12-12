Audit $ARGUMENTS for over-abstraction: prop drilling 3+ layers, type/mode switches, one-off helpers, logic scattered across 5+ files.

**$ARGUMENTS:** File path or component name (e.g., `src/components/PaymentFlow.vue`)

Apply **vue-conventions** and **project-philosophy** skills.

Simplify by passing richer objects, inlining trivial logic, merging multi-mode components, consolidating related logic. The main component should tell you 80% of what's happening. Extract only genuinely reusable code. Make it clear, not clever.
