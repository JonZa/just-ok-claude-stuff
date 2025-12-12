Run `gh pr view $ARGUMENTS --json reviews --jq '[.reviews | group_by(.author.login) | .[] | sort_by(.submittedAt) | last]'` to pull only the most recent review from each reviewer on PR #$ARGUMENTS.

Categorize feedback by domain. Review each item against project-philosophy — discard suggestions that are over-engineering or YAGNI violations.

Create a numbered list of specific recommendations that I can reference for implementation. Each should include the simplest fix that solves the actual problem.
