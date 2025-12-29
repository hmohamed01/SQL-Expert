# SQL Expert

A Claude Code skill for Microsoft SQL Server and T-SQL development expertise.

## Overview

This skill provides guidance for writing, optimizing, and debugging T-SQL queries. It covers advanced querying techniques, performance tuning, security best practices, and transaction management.

## Installation

Clone this repository, then copy the `sql-expert` folder to your skills directory:

### User-level (all projects)

**macOS/Linux:**
```bash
cp -r sql-expert ~/.claude/skills/
```

**Windows (PowerShell):**
```powershell
Copy-Item -Recurse sql-expert $HOME\.claude\skills\
```

### Project-level (current project only)

**macOS/Linux:**
```bash
cp -r sql-expert .claude/skills/
```

**Windows (PowerShell):**
```powershell
Copy-Item -Recurse sql-expert .claude\skills\
```

## Repository Structure

```
SQL-Expert/
├── README.md
└── sql-expert/                   # <- Copy this folder to your skills directory
    ├── SKILL.md                  # Main skill definition with core instructions
    └── references/
        ├── patterns.md           # Query patterns: CTEs, pagination, PIVOT, MERGE, window functions
        ├── performance.md        # Execution plans, parameter sniffing, Query Store, wait statistics
        ├── security.md           # SQL injection prevention, dynamic SQL, permissions, data masking
        ├── data-types.md         # Type selection, collation, precision/scale, storage optimization
        └── transactions.md       # Isolation levels, deadlocks, distributed transactions, sagas
```

## Usage

Once installed, Claude Code will automatically use this skill when you ask about:
- T-SQL query writing or optimization
- SQL Server stored procedures
- Database performance tuning
- Query execution plans
- SQL security and injection prevention

## SQL Server Version Support

The skill covers features from SQL Server 2016 through 2022, with version annotations where applicable.

## License

MIT
