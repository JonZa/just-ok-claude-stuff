Refactor $ARGUMENTS to extract reusable formatters/utilities and repeated markup into simple display components, keeping it pragmatic.

**$ARGUMENTS:** File path or component name (e.g., `src/components/BookingDetails.vue`)

Apply **vue-conventions** and **project-philosophy** skills.

Keep business logic and conditionals in the parent—explicit over implicit. Avoid "smart" multi-mode components. If it adds cognitive load without significant benefit, inline it. Optimize for: can I understand this in 6 months?
