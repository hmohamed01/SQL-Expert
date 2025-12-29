# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Claude Code skill for Microsoft SQL Server and T-SQL development. It contains no executable code—only markdown documentation that Claude Code loads when users ask about SQL Server topics.

## Repository Structure

```
SQL-Expert/
├── README.md              # Installation instructions
└── sql-expert/            # The skill folder (users copy this to their skills directory)
    ├── SKILL.md           # Main skill definition with frontmatter and core instructions
    └── references/        # Detailed reference documentation
        ├── patterns.md    # Query patterns (CTEs, pagination, PIVOT, MERGE, window functions)
        ├── performance.md # Execution plans, parameter sniffing, Query Store
        ├── security.md    # SQL injection prevention, dynamic SQL, permissions
        ├── data-types.md  # Type selection, collation, storage optimization
        └── transactions.md # Isolation levels, deadlocks, distributed transactions
```

## Skill Frontmatter

The `SKILL.md` file must have YAML frontmatter with `name` and `description` fields. The description determines when Claude Code activates this skill.

## Adding Content

When adding T-SQL examples or patterns:
- Include version annotations for features not available in all SQL Server versions (2016-2022)
- Show both anti-patterns (BAD) and correct approaches (GOOD) when demonstrating best practices
- Consider NULLs, empty results, and edge cases in examples
